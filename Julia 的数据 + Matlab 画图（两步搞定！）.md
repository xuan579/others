# Julia 的数据 + Matlab 画图（两步搞定！）

<font size=2>导语：习惯了使用 julia 进行编程，但是又看不惯 julia 那 low 到爆的画图方式？（就连 PtPlot.surf 的输入变量的顺序都不正常...）那就来使用 Matlab 吧！超简单！两步就可以完美搞定！不管你是想画2维图像还是3维图像，不管你想使用 plot 还是 surf !</font>



比如现在要将 julia 当中的数组 x 转移到 Matlab 中进行画图。

## Step1. 将Julia中的数据存储为 h5 文件	

下面的语句可以将数组 x 存储到 data.h5 文件中，默认与当前的程序文件在同一文件夹中。

```
using HDF5
h5open("data.h5", "w") do file
    write(file, "x", x) 
end
```

当然，也可以同时将多个数组存储到同一个h5文件中，只需要将上述对应语句改为

```
    write(file, "x", x, "y", y, z, "z") 
```

## Step2. 使用Matlab读取h5文件

Matlab 读取 h5 文件可直接通过 h5read 函数来实现，通过下面的语句

```
t = h5read('data.h5','/x');
```

就可以将 data.h5 文件中的 x 赋值给变量 t。 <font color = red>  注意：该语句中，反斜杠必不可少！！！</font>



现在，就去在 Matlab 里面自由地画图吧！



![](https://raw.githubusercontent.com/xuan579/others/main/freedom1.gif)

