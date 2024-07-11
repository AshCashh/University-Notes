---
Created: 2023-06-30T19:37:47+10:00
Modified: 2024-07-03T19:35:33+10:00
---
# Desktop Management


| s   | s   |     |     |
| --- | --- | --- | --- |
|     |     |     |     |

| Command                                                        | Syntax        | Description                                       |
| -------------------------------------------------------------- | ------------- | ------------------------------------------------- |
| [save](https://au.mathworks.com/help/matlab/ref/save.html)     | save data.mat | Save your current workspace to a MAT file         |
| [load](https://au.mathworks.com/help/matlab/ref/load.html)     | load data.mat | Load the variables in a MAT file to the workspace |
| [clear](https://au.mathworks.com/help/matlab/ref/clear.html)   | clear         | Clear all variables from the workspace            |
| [clc](https://au.mathworks.com/help/matlab/ref/clc.html)       | clc           | Clear all text from the command window            |
| [format](https://au.mathworks.com/help/matlab/ref/format.html) | format long   | Change how numeric output is displayed            |
Note: Loading and Saving also works for individual variables

# Built-in Functions & Constants 
MATLAB contains built-in functions & constants, below are a few examples:

|Constant   |Description   |
|---|---|
|[eps](https://au.mathworks.com/help/matlab/ref/eps.html)|Floating-point relative accuracy|
|[flintmax](https://au.mathworks.com/help/matlab/ref/flintmax.html)|Largest consecutive integer in floating-point format|
|[i](https://au.mathworks.com/help/matlab/ref/i.html)|Imaginary unit|
|[j](https://au.mathworks.com/help/matlab/ref/j.html)|Imaginary unit|
|[Inf](https://au.mathworks.com/help/matlab/ref/inf.html)|Create array of all `Inf` values|
|[pi](https://au.mathworks.com/help/matlab/ref/pi.html)|Ratio of circle's circumference to its diameter|
|[NaN](https://au.mathworks.com/help/matlab/ref/nan.html)|Create array of all `NaN` values|



The full list of all functions can be found [here](https://au.mathworks.com/help/matlab/referencelist.html?type=function&category=index&s_tid=CRUX_lftnav_function_index)

# Array Types
- A single number, called a scalar is represented by a 1-by-1 array.
- You can create arrays with multiple elements using square brackets. E.g. `[3,5]` or just `[3 5]`
- When you separate numbers using semicolons (;), it creates a column vector. E.g. `[1;3]`

| Example          | Description     |
| ----------------- | ------------- |
| 4                 | scalar        |
| [3,5]             | row vector    |
| [1;3]             | column vector |
| [3,4,5;6,7,8]     | matrix        |

## Array Operations
- You can add a scalar value to all the elements of an array. E.g. If `x = [1 2 3]`, `y = x + 2` then `y = [3 4 5]`
- You can add any two arrays of the same size. E.g. `z = x + y`
- You can multiply or divide all the elements of an array by a scalar. E.g. `z = 2 * x` or `y = x / 3`
- You can apply basic statistical functions to a vector to produce a single output. E.g. the max value of a vector can be determined using `xMax = max(x)`
- The `.*` operator performs element-wise multiplication. E.g. `z = [3 4] .* [10 20] = [30 80]`

| Example                         | Description                                      |
| -------------------------------- | --------------------------------------------- |
| [1 2 3] + 2.  ans = [3 4 5]         | Perform matrix multiplication
| [1 1 ; 1 1] \* [2 2 ; 2 2] ans = 4 4 ; 4 4         | Perform matrix multiplication                 |
| [1 1 ; 1 1] .\* [2 2 ; 2 2] ans = 2 2 ; 2 2        | Perform element-wise multiplication           |

# Evenly-Spaced Vectors
- An vector with evenly-spaced numbers can be created. E.g. `5 6 7 8`
- An alternative is to use the colon operator (:) and specify only the start and end values. E.g. `5:8`
- The colon operator uses a default spacing of 1. However, you can specify the spacing. E.g. `20:2:26`
- If you know the number of elements you want in a vector, you can use the `linspace` function. (`linspace(first,last,number_of_elements)`).
- To create linearly spaced column vectors, the transpose operator (') converts a row vector to a column vector. E.g. If `x = 1:3` the column vector is `x'`. To create in a single command: `x = (1:3)'`

| Example                 | Description                                              |
| ----------------------- | -------------------------------------------------------- |
| 1:4                     | Create a vector from 1 to 4, spaced by 1, using the colon (:) operator. |
| 1:0.5:4                 | Create a vector from 1 to 4, spaced by 0.5.               |
| linspace(1,10,5)        | Create a vector with 5 elements. The values are evenly spaced from 1 to 10. |

# Creating Matrices
- To create commonly used matrices, such as matrices of random numbers use the `rand` function. E.g. `rand(2)` will create a 2-by-2 matrix of random numbers. 
- Most array creation functions accept the same inputs as `rand`. E.g. the `zeros` and `ones` functions create matrices of all zeros and all ones.

| Example                 | Description                                                      |
| ----------------------- | ---------------------------------------------------------------- |
| rand(2)                 | Create a square matrix with 2 rows and 2 columns.                 |
| zeros(2,3)              | Create a rectangular matrix with 2 rows and 3 columns.            |

Note the `zeros` function can be replaced with any single digit function i.e. `ones`, `twos`, etc.

# Indexing
You can extract values from an array using row-column indexing:

| Example               | Description                                            |
| --------------------- | ------------------------------------------------------ |
| A(3,4)                | Access the element in the 3rd row of the 4th column.    |
| A(end,2)              | Access the element in the second column of the last row.|
| A(2,:)                | Access the entire second row.                           |
| A(1:3,:)              | Access all columns of the first three rows.             |
| A(2)=11               | Change the value of the second element in the array to 11.|

You can extract values from a vector using a single index value. E.g. `x = v(3)` returns the third element of row or column vector v.

# Multiple Outputs
- You can apply the `size` function to a vector or matrix to produce a single output variable containing the array size in a two-element row vector. E.g. `s = size(x) = [7 4]`
- You can request two output variables from the size function, where each variable contains the size of one of the dimensions of the input array. E.g. `[xrow, xcol] = size(x)` which equals to: `xrow = 7` and `xcol = 4`

| Example                           | Description                                                  |
| --------------------------------- | ------------------------------------------------------------ |
| [xrow,xcol]=size(x)               | Save the number of rows and columns in `x` to two different variables. |
| [xMax,idx]=max(x)                 | Calculate the maximum value of `x` and its corresponding index value. |

# Documentation

| Example                           | Description                                                  |
| --------------------------------- | ------------------------------------------------------------ |
| [doc](https://au.mathworks.com/help/matlab/ref/doc.html) randi               | Open the documentation page for the randi function |

# Plots

| Example       | Description                                                         |
|---------------|---------------------------------------------------------------------|
| [plot](https://au.mathworks.com/help/matlab/ref/plot.html)(x,y,"ro-","LineWidth",5)    | Plot a red (r) dashed (--) line with a circle (o) marker, with a heavy line width.  |
| hold on       | Add the next line to existing plot.                                 |
| hold off      | Create a new axes for the next plotted line.                        |
| title("MyTitle") | Add a title to a plot.                                              |
| ylabel("Mass") | Add a y label to a plot.                                              |
| legend("a","b") | Add a legend to a plot                                            |

[Line Properties](https://au.mathworks.com/help/matlab/ref/matlab.graphics.chart.primitive.line-properties.html)

# Tables

| Example                        | Description                                                           |
| ------------------------------ | --------------------------------------------------------------------- |
| data.HeightYards               | Extract the variable `HeightYards` from the table `data`.              |
| data.data.HeightMeters         | `data.HeightYards` multiplied by 0.9144 to derive the variable `HeightMeters` from existing data. |

# Logical Indexing
Relational operators such as $>, <, ==$  perform comparisons between two values. The outcome of a comparison for equality or inequality is either 1 (true) or 0 (false). Such logic can be used in arrays

| Example                        | Description                                                           |
| ------------------------------ | --------------------------------------------------------------------- |
| [5 10 15]>12                     | Compare a vector to the value 12.                                     |
| v1(v1>6)                       | Extract all elements in `v1` that are greater than 6.                  |
| x(x=.=999)=1                       | Replace all values in `x` that are equal to 999 with the value 1.                |

# Programming

| Example                        | Description                                                           |
| ------------------------------ | --------------------------------------------------------------------- |
| if x>0.5<br>y=3<br>else<br>y=4<br>end | If `x` is greater than 0.5, set the value of `y` to 3. Otherwise, set the value of `y` to 4. |
| for c=1:3<br>disp(c)<br>end    | The loop counter (`c`) progresses through the values 1 to 3 (1, 2, and 3). The loop body displays each value of `c`. |

