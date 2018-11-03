# Bash

## 扯淡

Python脚本中经常结合各种脚本，熟练掌握Bash也是一项必须技能。

## 常用变量

- $0，shell文件名，例如bash ./data/mnist/get_mnist.sh，这里$0表示./data/mnist/get_mnist.sh；
- \$1-$n，参数1-参数n；

## 文件

- 获取当前文件目录
```
pwd -P # -P选项对于软链接也有用
```
- 跳转到脚本所在位置
```
cd $(dirname "$0")
```
- 获取当前文件中的文件
```
for d in */ ; do
    echo "$d"
done
```

## 字符串
- 包含字串
```
string='My long string'
if [[ $string = *"My long"* ]]; then
  echo "It's there!"
fi
```

## 参考资料
- [Advanced Bash-Scripting Guide](http://www.tldp.org/LDP/abs/abs-guide.pdf)，高级Bash脚本指南，后面主要参考这个系统学习。
- [How can I get the current working directory? [duplicate]](https://unix.stackexchange.com/questions/188182/how-can-i-get-the-current-working-directory)
- [linux中shell变量$#,$@,$0,$1,$2的含义解释](http://www.cnblogs.com/fhefh/archive/2011/04/15/2017613.html)
- [How do I loop through only directories in bash?](https://unix.stackexchange.com/questions/86722/how-do-i-loop-through-only-directories-in-bash)