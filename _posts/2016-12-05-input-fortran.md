---
title: Using flexible input files in Fortan
date: 2016-12-05
excerpt: "Input processing made easier"
header:
  overlay_image: /images/code.jpg
  overlay_filter: 0.5
use_math: false
classes: wide
---

One thing that I don't like about coding stuff in FORTRAN compared to higher level languages is the low flexibility to process input from a file.

A smart way to go around the problem would be to use a more script-oriented language to process the input before feeding it into your FORTRAN code to do the actual computation.

When I was writing my PhD, I instead wrote a piece of code that uses only FORTRAN to get there. I share it in its own [GitHub repository](https://github.com/jrekier/inputf90).

Here I go through the pieces of this code.

I start by defining a custom type with one component to stock the name of the input and one for its value

```fortran
type inputtype
     character(len=30) :: name
     character(len=100), allocatable, dimension(:) :: val
end type inputtype
type(inputtype), allocatable, dimension(:) :: input
```

Then the following routine goes through the input file and counts the number of inputs ignoring blank lines and comment lines starting with a '#'


```fortran
contains
  subroutine read_input(input_file)
    implicit none
    character(len=*), intent(in) :: input_file
    character(len=2048) :: buffer, label, str, fmt
    integer :: pos, ios, cnt, i, numb_input

    ios = 0
    cnt = 0
    i = 1
    numb_input = 0

    open(10,file=input_file,status='old')

    do while (ios == 0) ! count the number of inputs
       read(10, '(A)', iostat=ios) buffer
       if(ios == 0)then

          ! Find the first instance of whitespace. Split label and data.
          pos = scan(buffer, ' ')
          label = buffer(1:pos)

          if((label=='') .or. (label( :1)=='#'))cycle  ! skip line if blank or commented with '#'
          numb_input = numb_input + 1
       endif
    end do
    rewind(10)
    ios = 0  

    allocate(input(numb_input))  
```

Then it goes through the file again, collects inputs and stack them in the memory with the appropriate type defined above.

```fortran
do while (ios == 0) ! read input
   read(10, '(A)', iostat=ios) buffer
   if(ios == 0)then

      ! Find the first instance of whitespace. Split label and data.
      pos = scan(buffer, ' ')
      label = buffer(1:pos)
      buffer = buffer(pos+1:)

      if((label=='') .or. (label( :1)=='#'))cycle  ! skip line if blank or commented with '#'

      str = buffer

      fmt = '(a'
      cnt = 0
      do while((pos/=0).and.(pos/=1))
         pos = scan(trim(adjustl(str)), ' ')
         str = trim(adjustl(str(pos+1:)))
         cnt = cnt + 1
         fmt = trim(adjustl(fmt)) // ',X,a'
      enddo

      fmt = trim(adjustl(fmt)) // ')'

      input(i)%name = label
      allocate(input(i)%val(cnt))
      if(cnt==1)then
         read(buffer, '(a)', iostat=ios) input(i)%val
      else
         read(buffer, trim(adjustl(fmt)), iostat=ios) input(i)%val
         read(buffer, *, iostat=ios) input(i)%val
      end if

      i=i+1

   endif
end do
close(10)
```

The rest of the file consists in functions to assign an input to a specific variable with a specific type. Here is the one to assign the input value to a double precision real number.
The functions takes two arguments on top of the variable's name. If there is only one input in the list, the variable provided as the first argument gets populated with the corresponding value and the second one is returned as an empty array. In case there is more than one input, it goes the other way around and it's the variable in the second arguments that gets populated.

```fortran
subroutine assign_real(var,var_array,name)
  implicit none
  real(kind=8), intent(out) :: var
  real(kind=8), allocatable, dimension(:), intent(inout) :: var_array
  character(len=*), intent(in) :: name
  integer :: i, j
  logical :: flag

  flag = .false.
  do i=1, size(input)
     if(input(i)%name==name) then
        allocate(var_array(size(input(i)%val)))
        do j=1, size(input(i)%val)
           !print*,input(i)%name,trim(adjustl(input(i)%val(j)))
           read(input(i)%val(j),*) var_array(j)
        enddo
        flag = .true.
     end if
  enddo
  if(flag.eqv..false.) then
     allocate(var_array(0))
     print*, 'Warning : no matching of label "', trim(adjustl(name)), '" found in input file'
  endif

  var = 0d0
  if(size(var_array)==1) then
     var = var_array(1)
  endif
end subroutine assign_real
```

The GitHub repository contains an easy example presenting all the features.
