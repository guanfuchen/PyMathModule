# Julia

增加Julia学习线性代数相关知识。

---
## 安装Julia

### Mac

```
brew cask install julia
```

## 安装IJulia
安装IJulia kernel，在notebook中使用。

```
ENV["JUPYTER"]="/usr/local/bin/jupyter"
Pkg.add("IJulia")
```

## 安装PyPlot
安装PyPlot进行绘图。
```
ENV["PYTHON"]="/usr/bin/python"
Pkg.build("PyCall")
```

---
## 参考资料

[Linear Algebra](http://julia-cn.readthedocs.io/zh_CN/latest/stdlib/linalg/#stdlib-linalg) Julia中线性代数知识。

[Julia 中文手册](http://wiki.jikexueyuan.com/project/julia-manual/begining.html) 极客学院中有关Julia的中文文档翻译。

[julialang](https://julialang.org/) Julia主页。

[IJulia.jl](https://github.com/JuliaLang/IJulia.jl) IJulia github主页。

[Julia's tours](http://www.numerical-tours.com/julia/) 其中包含了大量Julia在特定领域的实践。

[Online tutorials](https://julialang.org/learning/)

[PyPlot.jl](https://github.com/JuliaPy/PyPlot.jl) Julia中plot绘图库。
