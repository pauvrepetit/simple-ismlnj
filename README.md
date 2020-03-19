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

解决了一个小问题
    
这个jupyter的内核实际上就是调用sml命令向其中送入在jupyter中输入的表达式，然后将sml的输出通过jupyter显示出来
由于sml命令使用"- "作为等待用户输入命令的提示符，因此使用这个字符串作为分隔符从sml的输出中读取数据，当我们输入下面的sml语言命令时，将会出现一些问题(当然
，这是在输入的命令不能够正确执行的情况下发生的)
- fun add n = (n + 1);
- add (-1);
sml中使用~作为负号，我们错误的使用了-符号，因此sml会报错，在错误信息中会出现字符串"- "，这将导致jupyter内核错误的截取sml的输出信息，导致在其后面执行的所
以命令都会输出不对应的输出信息。
我们将分隔符由"- "修改为"\n- "，强制要求"- "出现在一行的开头，sml在正确执行的情况下，应该是不会在一行的开头输出"- "字符串的，而对于报错的情况，报错的信息存在一个缩进，因此可以解决这样一个问题。