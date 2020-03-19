# simple-ismlnj
forked from matsubara0507/simple-ismlnj   
   
#### A Jupyter Kernel for Standard ML Language

## install
创建一个内核 名字为sml
``` shell
ipython3 kernel install --name sml
```
查看内核安装的位置
``` shell
jupyter kernelspec list
```
在sml内核对应的目录下有一个名为kernel.json的文件，该文件由ipython3创建

用此项目中的kernels/smlnj/kernel.json替换该目录下默认的kernel.json文件

修改该文件，将argv中的第二个参数修改为此项目中的smlnjkernel.py文件的路径
