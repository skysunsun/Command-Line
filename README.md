# Command-Line

# conda 换源操作
----
## 清华源：

conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/<br>
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/<br>
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/<br>
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/<br>
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/bioconda/<br>
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/menpo/<br>
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/<br>
conda config --set show_channel_urls yes<br>

## 中科大源:

conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/main/<br>
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/free/<br>
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/conda-forge/<br>
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/msys2/<br>
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/bioconda/<br>
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/menpo/<br>
conda config --set show_channel_urls yes<br>


## conda换回默认源

conda config --remove-key channels


## 手动编辑

gedit ~/.condarc<br>
source ~/.condarc<br>

# conda 环境操作

### 创建一个名为python34的环境，指定Python版本是3.4（不用管是3.4.x，conda会为我们自动寻找3.4.x中的最新版本）
conda create--name python34 python=3.4

### 安装好后，使用activate激活某个环境
activate python34# for Windows
source activate python34# for Linux & Mac
### 激活后，会发现terminal输入的地方多了python34的字样，实际上，此时系统做的事情就是把默认2.7环境从PATH中去除，再把3.4对应的命令加入PATH

### 此时，再次输入
python --version
### 可以得到`Python 3.4.5 :: Anaconda 4.1.1 (64-bit)`，即系统已经切换到了3.4的环境

### 如果想返回默认的python 2.7环境，运行
deactivate python34  # for Windows
source deactivate python34  # for Linux & Mac

### 复制一个环境
conda create -n pyhon34 --clone python34clone
### 删除一个已有的环境
conda remove --name python34 --all
### 为了确定这个环境已经被移除，输入以下命令
conda info -e

### 查看当前环境下已安装的包
conda list

### 查看某个指定环境的已安装包
conda list -n python34

### 查找package信息
conda search numpy

### 安装package
conda install -n python34 numpy
### 如果不用-n指定环境名称，则被安装在当前活跃环境
### 也可以通过-c指定通过某个channel安装# 查看当前环境下已安装的包
conda list

### 查看某个指定环境的已安装包
conda list -n python34

### 查找package信息
conda search numpy

### 安装package
conda install -n python34 numpy
### 如果不用-n指定环境名称，则被安装在当前活跃环境
### 也可以通过-c指定通过某个channel安装

### 更新package
conda update -n python34 numpy

### 删除package
conda remove -n python34 numpy
前面已经提到，conda将conda、python等都视为package，因此，完全可以使用conda来管理conda和python的版本，例如

### 更新conda，保持conda最新
conda update conda

### 更新anaconda
conda update anaconda

### 更新python
conda update python
### 假设当前环境是python 3.4, conda会将python升级为3.4.x系列的当前最新版本

[参考博客](https://blog.csdn.net/ztf312/article/details/65448597)


# 编辑环境变量

gedit ~/.bashrc

立即生效

source ~/.bashrc
# pip源更改

## 临时使用： 
pip 后加参数 -i https://pypi.tuna.tsinghua.edu.cn/simple <br>
例：pip install -i https://pypi.tuna.tsinghua.edu.cn/simple pandas 
## 永久使用： 
### Linux下： 
修改 ~/.pip/pip.conf (没有就创建一个)， 修改 index-url至tuna，内容如下：

    [global]
    index-url = https://pypi.tuna.tsinghua.edu.cn/simple

### windows下: 
直接在user目录中创建一个pip目录，如：C:\Users\xxxx\pip，新建文件pip.ini，内容如下

    [global]
    index-url = https://pypi.tuna.tsinghua.edu.cn/simple
[参考博客](https://blog.csdn.net/sxf1061926959/article/details/54091748)
