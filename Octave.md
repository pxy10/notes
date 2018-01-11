
## Octave Programing Notes

### basic syntax

`length()`, 返回最大的维度

`pwd`, return current directory

`cd`, `ls`

`who`, list all current variables; `whos` shows more details

`M([1 3], :)` 返回第一和第三行

`M = [M, newvector]` appends another column vector to right

`M(:)` puts all elements of `M` into a single vector

`addpath('pathyouwanttoaddintosearchpath')` adds into search path.

### load/save file

`load filename.dat` or `load('filename.dat')`

If `M` is a matrix, `save matrix.mat M` can help save `M` into `matrix.mat` binary file

`save matrix.txt M -ascii` can help save `M` into `matrix.txt` text file


### plot

After plotting a figure, using `cd directory_you_want; print -dpng 'myPlot.png'` to save figure.

`close` helps close current plot.

`imagesc(M)` helps check the elements of matrix `M`; `imagesc(M), colorbar, colormap gray;`
