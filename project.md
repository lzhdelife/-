# PyTorch

搭建环境

https://blog.csdn.net/wyf2017/article/details/118676765

环境配置细节

[Conda虚拟环境](https://blog.csdn.net/fs1341825137/article/details/109681541)

[jupyter server](https://blog.csdn.net/fs1341825137/article/details/109683965)

```bash
source /home/lzh/anaconda3/etc/profile.d/conda.sh

conda create -n pytorch-test

conda activate pytorch-test
```


To list all existing Anaconda virtual environments, you can use the following command in your terminal or command prompt:

```
bashCopy code
conda env list
```



## jupyter

ipykernel 是 jupyter 的一种内核

ipykernel 或者 jupyter可以安装在conda虚拟环境下



检查ipykernel是在哪个conda环境下

在 Linux 终端中

```bash
conda activate deeplearning	# xian
jupyter kernelspec list
```

在 jupyter notebook 中

```python
import sys
sys.executable
```



### conda install jupyter 和 conda install ipykernel的区别

`conda install jupyter` 和 `conda install ipykernel` 有一些区别，尽管它们都与 Jupyter 相关联：

1. **安装范围**：
   - `conda install jupyter`：安装了整个 Jupyter 套件，包括 Jupyter Notebook、JupyterLab、Jupyter Console 等。
   - `conda install ipykernel`：只安装了 Jupyter 的 IPython 内核（ipykernel），它是 Jupyter 笔记本和 JupyterLab 的后端引擎之一。
2. **功能**：
   - `conda install jupyter`：安装了 Jupyter 的完整功能，包括创建、编辑和运行 Jupyter 笔记本，以及在 JupyterLab 中进行更高级的交互式计算和数据分析。
   - `conda install ipykernel`：安装了 IPython 内核，允许您在 Jupyter 笔记本中运行 Python 代码。
3. **依赖关系**：
   - `conda install jupyter`：会安装 Jupyter 所需的所有依赖项，包括 IPython 内核和其他相关包。
   - `conda install ipykernel`：只会安装 IPython 内核，不包含其他 Jupyter 组件。

通常情况下，如果您希望在 Jupyter 笔记本中使用 Python 内核，则只需要安装 `ipykernel`。但如果您希望使用完整的 Jupyter 套件，包括 JupyterLab 等，则需要安装 `jupyter`。



# SSH

ssh -p 39709 lzh@115.236.153.170

ssh -p 8025 lzh@8.134.251.252

ssh -p 22 root@8.134.251.252



## 配置ssh免密登录

本地访问远程服务器

本地用户路径 下 `.ssh/` 下有文件`id_rsa.pub`，将此文件的内容复制到

远程服务器`~/.ssh/authorized_keys`文件中

如果没有这个文件，则手动创建

1. **Create the `.ssh` directory (if it doesn't exist)**:

   ```
   bashCopy code
   mkdir -p ~/.ssh
   ```

2. **Create the `authorized_keys` file**:

   ```
   bashCopy code
   touch ~/.ssh/authorized_keys
   ```

3. **Set appropriate permissions**:

   ```
   bashCopy codechmod 700 ~/.ssh
   chmod 600 ~/.ssh/authorized_keys
   ```

4. **Paste your public key into the `authorized_keys` file**:

   Open the `id_rsa.pub` file, copy its contents, and paste it into `~/.ssh/authorized_keys`.

5. **Save the file**.

接下来本地就可以免密ssh登录远程服务器了



# 阿里云

8.134.251.252(公)

172.23.12.171(私有)

### 开放端口

1.在安全组中添加

https://developer.aliyun.com/article/1209367

2.在服务器中开放

```bash
 sudo systemctl status firewalld
 udo systemctl start firewalld
 sudo firewall-cmd --zone=public --add-port=8025/tcp --permanent
 sudo firewall-cmd --reload
 sudo firewall-cmd --list-ports
```



# 内网穿透

NPS

教程

https://youtu.be/jdVQQQacPj4?si=c6wj9VGfnFm4MYRa

[内网穿透服务器搭建教程，带WEB管理 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/485703115)

https://post.smzdm.com/p/a07md2nr/


买一个有公网IP的服务器

在NPS官网下载服务端和客户端

https://github.com/ehang-io/nps/releases

<img src="image\1712411889827.jpg" alt="下载地址" style="zoom:50%;" />



查处理器架构

```bash
uname --machine
```

在购买的有公网IP的服务器上下载server

在内网中的服务器上下载client

剩下的看官方教程

### 阿里云开放端口

1.在安全组中添加

https://developer.aliyun.com/article/1209367

2.在服务器中开放

```bash
 sudo systemctl status firewalld
 udo systemctl start firewalld
 sudo firewall-cmd --zone=public --add-port=8025/tcp --permanent
 sudo firewall-cmd --reload
 sudo firewall-cmd --list-ports
```

### 项目中用到的端口介绍

8080：服务端管理页面的端口

8024：服务端暴露给客户端，与客户端连接的端口

8025（自定义）：服务端暴露在外，ssh远程访问的端口

因此，ssh连接 公网IP:8025，即可访问到 内网IP:22



ssh连接

```bash
ssh -p 8025 dell@8.134.251.252
# 登录 8.134.251.252:8025  账号 dell 密码 admin
```



# 论文项目



```bash
sudo git clone https://github.com/lzhdelife/CrosSCLR.git /home/lzh/Project/CrosSCLR --progress
```





# OpenAI

国内连API

https://zhuanlan.zhihu.com/p/655954134



## python server

```bash
python -m http.server
python -m http.server PORT

```











# python venv

**创建虚拟环境**：

在终端中，导航到项目目录，然后运行以下命令来创建虚拟环境：

```bash
python -m venv .venv
```

这将在当前目录创建一个名为 `venv_name` 的虚拟环境。

**激活虚拟环境**：

在 Linux 和 macOS 上：

```bash
source .venv/bin/activate
```

在 Windows 上：

```bash
.venv\Scripts\activate
```

当虚拟环境激活时，终端提示符会显示虚拟环境名称，表示你现在正在虚拟环境中工作。

**安装依赖项**：

在虚拟环境中，你可以使用 `pip` 安装依赖项，这些依赖项将仅在此虚拟环境中可用。

pip换源

```bash
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```

```bash
pip install -r requirements.txt
```



**退出虚拟环境**：

通过运行以下命令退出虚拟环境：

```bash
deactivate
```



**自动生成requirement.txt**

```bash
pip freeze > requirements.txt
```





# WSL

```bash
wsl --install
```

重启电脑后，搞一个账号和密码

WSL Docker

## Git

```bash
git config --global user.name "lzhdelife"
git config --global user.email "lzhdelife@163.com"
```

1. **检查是否已经存在 SSH 密钥**：

   在终端中运行以下命令来检查是否已经存在 SSH 密钥：

   ```
   bashCopy code
   ls -al ~/.ssh
   ```

   如果您看到 `id_rsa` 和 `id_rsa.pub` 这样的文件，则表示您已经拥有 SSH 密钥。

2. **生成 SSH 密钥**：

   如果您在上一步中没有找到 SSH 密钥，可以通过运行以下命令来生成一个新的 SSH 密钥：

   ```
   cssCopy code
   ssh-keygen -t rsa -b 4096 -C "lzhdelife@163.com"
   ```

   在此命令中，将 `your_email@example.com` 替换为您在 GitHub 上注册的电子邮件地址。一路按回车键，直到完成密钥生成过程。

3. **将 SSH 公钥添加到 GitHub 帐户**：

   打开 `id_rsa.pub` 文件并复制其中的内容。您可以使用文本编辑器打开该文件，如 Vim 或 Nano。

   ```
   vi .ssh/id_rsa.pub
   ```

   然后，登录到您的 GitHub 帐户，导航到 "Settings" -> "SSH and GPG keys" -> "New SSH key"，将复制的公钥粘贴到 "Key" 字段中并保存。

4. **测试 SSH 连接**：

   运行以下命令来测试您的 SSH 连接是否成功：

   ```
   cssCopy code
   ssh -T git@github.com
   ```

   如果一切顺利，您应该会看到一条消息，确认您已成功连接到 GitHub。



## Python WSL

wsl 里的 python 需要写为 python3

打印python路径

```
lzhdelife@lzhdelife:~$ python3 -c "import sys; print(sys.executable)"
/usr/bin/python3
```



**安装pip**

接下来是安装pip： `sudo apt install python3-pip`

然后遇到了这个报错：E: Package 'python3-pip' has no installation candidate

我按照【2】的解决办法，首先运行命令：sudo apt-get update

然后再运行命令：sudo apt-get upgrade

然后再重新执行命令：`sudo apt install python3-pip`

然后就成功运行安装了pip。



# Docker



```bash
docker scout quickview

# check the container
docker ps
# check the images
docker images
```



## buile image



## docker run/exec

show the containers whether the container Up or Exited

```bash
docker ps -a
```

output:

```
CONTAINER ID   IMAGE                             COMMAND                  CREATED          STATUS                    PORTS                      NAMES
7e1f930cdc16   ubuntu                            "/bin/bash"              23 hours ago     Up 36 seconds
                    vigilant_cerf
608d2791fc5f   ubuntu                            "/bin/bash"              23 hours ago     Up 22 hours
                    cranky_curie
```



## docker run

以下是 `docker run` 命令中使用的参数的简要介绍：

1. `-d` 或 `--detach`：
   - 后台运行容器，即使您退出终端也能保持运行。
2. `--name <容器名称>`：
   - 为容器指定一个名称。
3. `-v <本地目录>:<容器目录>`：
   - 挂载一个本地目录到容器中，使容器内的数据可以持久化保存到本地文件系统上。本地目录与容器目录之间用冒号分隔。
4. `-p <主机端口>:<容器端口>`：
   - 将主机上的端口映射到容器中。主机端口与容器端口之间用冒号分隔。
5. `<镜像名称>`：
   - 要运行的容器的镜像名称。

现在，让我将这些参数应用到您的具体情况中：

```
bashCopy codedocker run -d \
  --name download \
  -v ./data:/data \
  -p 7860:7860 \
  <download_image_name>
```

- `-d`：后台运行容器。
- `--name download`：为容器指定名称为 "download"。
- `-v ./data:/data`：将当前目录下的 "data" 目录挂载到容器内的 "/data" 目录。
- `-p 7860:7860`：将主机的端口 7860 映射到容器的端口 7860。
- `<download_image_name>`：要运行的容器的镜像名称。

您需要将 `<download_image_name>` 替换为您下载服务的实际镜像名称。



交互式运行容器

```bash
docker exec -it 7e1f930cdc16 /bin/bash
```



## docker python



docker 是分层的，python镜像底层是Linux系统，

以下命令可以进入 python 镜像底层的Linux系统

```bash
docker exec -it 容器名 /bin/bash
```

进入这个Linux后，进入python环境，打印python安装路径，即可看到python安装在哪里

```shell
root@5964dfb7a22e:/# python3
Python 3.11.4 (main, Jul 28 2023, 05:02:22) [GCC 12.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> print(sys.executable)	// 打印python安装路径
/usr/local/bin/python3
```

也可以打印操作系统名称版本等

```bash
root@WorkPC:~# docker exec -it 5964dfb7a22e python3
Python 3.11.4 (main, Jul 28 2023, 05:02:22) [GCC 12.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import platform
>>> print(platform.system())
Linux
>>> print(platform.release())
5.15.90.1-microsoft-standard-WSL2
```



## 删除容器

```bash
docker rm <容器ID1> <容器ID2> <容器ID3> ...
```



## 给docker传输文件





## wsl  vscode  docker

```bash
 *  Terminal will be reused by tasks, press any key to close it. 

 *  Executing task: docker run --rm -d  helloworld:latest 

7120a9651b11d1b77aecf8d10295ffb2e59f98b0af2b13e6fe5b45d49200136f
 *  Terminal will be reused by tasks, press any key to close it. 
```





# 服务器

用户：dell	密码：admin

默认安装好的linux没有设置root密码，默认没有激活root用户

设置root密码

```bash
sudo passwd root
```

设置密码为：root



## vi/vim



## ssh

### 检查ssh是否安装

在 Ubuntu 或者 Debian 上，你可以运行以下命令检查 OpenSSH 软件包是否已安装：

```
bashCopy code
dpkg -l | grep openssh-server
```

如果软件包已安装，你会看到类似以下输出：

```
cssCopy code
ii  openssh-server          [版本号]          amd64        secure shell (SSH) server, for secure access from remote machines
```

如果没有安装 OpenSSH 软件包，你将不会看到任何输出。

## vscode远程连接

ssh lzh@115.236.153.177 -p 35035



## linux 基础命令

复制

```bash
sudo passwd root
```


### bash脚本

授予脚本执行权限：

```bash
chmod +x your_script_name.sh
```
运行脚本：
```bash
./your_script_name.sh
```

### 解压


```bash
tar -xzvf myfiles.tar.gz

unzip your_archive.zip
```







# 自监督学习







## Transformer

超详细图解Self-Attention
https://zhuanlan.zhihu.com/p/410776234

经典讲解
http://jalammar.github.io/illustrated-transformer/

LSTM
http://colah.github.io/posts/2015-08-Understanding-LSTMs/



### transformer与时空轨迹

在时空预测中，我们需要同时考虑时间依赖性和时空依赖性来进行准确的预测。Traffic Transformer [GIS 2020] 设计了一个编码器-解码器结构，使用自注意力模块来捕获时间-时间依赖关系，并使用图神经网络模块来捕获空间依赖关系。

用于交通流预测的Spatial-Temporal Transformer [Arxiv 2020] 网络更进一步，除了引入时间 Transformer 模块来捕获时间依赖关系外，它还设计了一个空间 Transformer 模块来辅助图卷积网络捕获更多的空间空间依赖关系。

此外，Spatial-Temporal Graph Transformer [ECCV 2020] 网络设计了一种基于注意力的图卷积机制来学习更复杂的时空注意力模式，以改进行人轨迹预测。

## 决策树

### Graphviz安装及使用-决策树可视化

https://zhuanlan.zhihu.com/p/268532582

除了pip install graphviz，还要从官网下载graphviz并配置环境变量

还需要在代码里加入

```python
import graphviz
import os 
# 以下这两行是手动进行环境变量配置，防止在本机的环境变量部署失败 
os.environ['PATH'] = os.pathsep + 'D:\\Graphviz\\bin' 
```





决策树CART 代价复杂度剪枝

https://blog.csdn.net/WANGWUSHAN/article/details/108556371



鸢尾花多分类

https://blog.csdn.net/sunxmwebstudy/article/details/112967313

https://blog.csdn.net/lys_828/article/details/122045161

## 模型导出

你可以使用以下命令来安装独立的`joblib`库：

```python
pip install joblib
```

一旦你安装了独立的`joblib`库，你可以使用它来导出和加载`scikit-learn`模型，就像我之前提到的那样。以下是使用外部`joblib`库版本导出和加载模型的示例代码：

```python
import joblib

# 导出模型
joblib.dump(model, 'model_filename.pkl')

# 加载模型
loaded_model = joblib.load('model_filename.pkl')
```



## 数据处理





## SQLToDB

2,207,171行 1238秒，20分钟





# pandas

## 统计

https://blog.csdn.net/qq_18351157/article/details/105993752



某一列单一元素

```python
column = 'groupsid'
groupsid_list = df_manager[column].unique().tolist()
# print(groupsid_list)
```

group by 统计

```python
category_stat = df['category'].value_counts()
print(category_stat)
type_stat = df['type'].value_counts()
print(type_stat)
actionway = df['actionway'].value_counts()
print(actionway)
```



## 读写文件

读文件

```python
column_names = ['Column1', 'Column2', 'Column3']
df = pd.read_csv('your_file.csv', header=None, names=column_names)
```



```python
input_file = 'TS_MARKTOOLS_GROUPTARGET.csv'
df = pd.read_csv(input_file)
loc_list = ['disknum','groupid', 'actualtime', 'property', 'longitude','latitude', 'height', 'speed', 'course']
df_group = df.loc[:, loc_list]
```

写文件

```python
filename = 'df_group_select.csv'
# 将 DataFrame 写入 CSV 文件
df_group.to_csv(filename, index=False)
```



## 增删改查

增加

```python
# 添加一列 disknum = 'dc51cfe41bda4eadaed0a7c6254a3a9e'
df_cluster['disknum'] = 'dc51cfe41bda4eadaed0a7c6254a3a9e'
```



定值筛选，排序，重置序号

```python
condition = df_group['disknum'] == disknum
df_group = df_group[condition]
df_group = df_group.sort_values('actualtime').reset_index(drop = True)
```

范围筛选

```python
# 选择groupsid 在 groupid_list 中的数据
groupsid_filter = df_label['groupsid'].isin(groupsid_list)
df_label = df_label[groupsid_filter].reset_index(drop=True)
```

删除

```python
# 删除['category', 'type', 'actionway']列中含有空值的行
df = df.dropna(subset=['category', 'type', 'actionway']).reset_index()


# 如果你希望删除所有列中含有空值的行，可以简单地使用下面的语句
df = df.dropna()

```



## group by

每个组取一行数据

```python
column_name = 'groupsid'
grouped = df.groupby(column_name)
# 获取每个组的第一行数据
df = grouped.first().reset_index()
```



## 遍历

```python
for index, row in df_newtable.iterrows():
    # Access data in specific columns for the current row
    column1_value = row['column1']
    column2_value = row['column2']
```







## sklearn画图

包 scikit-plot，简写为 skplt

```python
import matplotlib.pyplot as plt
import scikitplot as skplt
```



### sklearn 常用数据及可视化

https://blog.csdn.net/qq_42929168/article/details/122329904



分类（监督学习）结果可以用混淆矩阵展示

```python
import scikitplot as skplt
skplt.metrics.plot_confusion_matrix(y, predictions, normalize=True)
```





多分类

ovo，ovr

[(63条消息) 多分类问题OVR和OVO----机器学习_ovo多分类问题_卷了个积寞的博客-CSDN博客](https://blog.csdn.net/qq_45997545/article/details/109409178)



DBSCAN算法

https://zhuanlan.zhihu.com/p/340361548

[聚类综述，概念，算法](https://zhuanlan.zhihu.com/p/104355127)



4/7

已完成工作

一、连接Group和Label两张表中的时间

Label是Group数据的标签，但这两种数据在不同表中，且较难对应，因为（1）时间分别使用了两种格式（2）Label表中的members字段没有拆分

本周完成了两张表的时间对应，Label表中的时间（labeltime）格式为时分秒，是在态势系统中回放时记录的时间，Group表中的时间（actualtime）为墨子导出的int类型的数据（35252--36392）。根据比例将两种时间作了近似对应。members字段拆分尚未完成，拆分后即可与Group表进行连接。本周数据处理效果如图1所示。

![image-20230407123914565](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230407123914565.png)

二、理解sklearn中文文本多分类代码



实验分析

168000条数据有130000条未知

存在的问题



进一步工作计划

跑通文本多分类代码，为实现识别Group表中property字段（型号）做准备



## 文本多分类

[使用python和sklearn的中文文本多分类实战开发](https://blog.csdn.net/weixin_42608414/article/details/88046380)





## 聚类和分类的区别

分类简单来说，就是根据数据的特征或属性，划分到已有的类别中。也就是说，这些类别是已知的，通过对已知分类的数据进行训练和学习，找到这些不同类的特征，再对未分类的数据进行分类。

聚类是不知道数据会分为几类，通过聚类分析将数据或者说用户聚合成几个群体，那就是聚类了。聚类不需要对数据进行训练和学习。

分类属于监督学习，聚类属于无监督学习。常见的分类比如决策树分类算法、贝叶斯分类算法等聚类的算法最基本的有系统聚类，K-means均值聚类



### 机器学习分类算法简单介绍：

[一文读懂机器学习分类算法（附图文详解） - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/82114104)

图文讲解了KNN，SVM，朴素贝叶斯等，很多是单标签二分类。结合项目要求集群类别有多种，标签也有集群类别、行动类别、行动方式三种。所以对多分类，多标签作进一步了解。



本项目研究的内容属于机器学习中的分类问题。分类区别于聚类，属于监督学习。需要分类的数据本身已有标签



机器学习中的分类，二分类、多分类、多标签分类

![img](https://pic3.zhimg.com/80/v2-17fc3f1708f0cc89af85bfbdaed1f646_720w.webp)
多分类：新闻可以分为体育、财经、其它等三个类别，这就是一个典型的多分类任务。

![img](https://pic1.zhimg.com/80/v2-5df2aa7989671d5bb3815670cb0e5690_720w.webp)



多标签分类：每个样本可以预测为一个或多个类别

三种标签：

**集群类别**：打击集群，干扰集群，巡逻集群，掩护集群，预警集群，侦查集群，训练集群  

**行动类别**：联合护航，联合兵力投送，联合搜救，联合战场遮断，联合火力封锁，空中截击，空中突击，空中巡逻

**行动方式**：正面，侧翼，钳行，多点


![img](https://pic4.zhimg.com/80/v2-9c473d1810c51ff4a6c80058e208291b_720w.webp)

来源：[二分类、多分类、多标签分类的基础、原理、算法和工具 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/270458779)



## 需求：战场集群划分

战场集群划分是分类问题还是聚类问题

## 技术方案

1、先划分集群类别，

2、先根据



# MySQL

**安装**

**MySQL 未安装**：如果 MySQL 尚未安装在系统上，则不会有相应的服务单元。你可以尝试安装 MySQL 服务器。在大多数 Linux 发行版上，可以使用包管理器来安装 MySQL。例如，在 Ubuntu 上，你可以使用以下命令安装 MySQL：

```
bashCopy codesudo apt-get update
sudo apt-get install mysql-server
```

**修改密码**

1. 使用以下命令登录到 MySQL 服务器：

   ```
   bashCopy code
   sudo mysql
   ```

2. 登录后，执行以下命令更改 root 用户的密码：

   ```
   sqlCopy code
   ALTER USER 'root'@'localhost' IDENTIFIED BY 'new_password';
   ```

   在这里，`new_password` 应该是你要设置的新密码。

3. 重启 MySQL 服务以应用更改：

   ```
   bashCopy code
   sudo systemctl restart mysql
   ```

**查状态**

**MySQL 服务器未运行**：首先确保 MySQL 服务器正在运行。你可以使用以下命令检查 MySQL 服务器的状态：

```
bashCopy code
systemctl status mysql
```

如果 MySQL 服务器未运行，你可以使用以下命令启动它：

```
bashCopy code
systemctl start mysql
```





# Oracle

Oracle与MySQL

Oracle适合数据量较大的数据库



ORA-01017: invalid username/password; logon denied Oracle数据库报错解决方案一

https://blog.csdn.net/qq_16183731/article/details/83864811



## 用户创建

```sql
conn sys/root as sysdba					# 登录超级管理员

select instance_name from v$instance;	# 连接实例

create tablespace scott_tb_space datafile 'd:/tbspace/scott_tb_space.dbf' size 200m;	# 创建表空间

create user scott identified by tiger default tablespace scott_tb_space;	# create user
#		      |					  |
#		  user name			   password

grant dba to scott;		# 用户一开始是没有权限的，需要授权

select * from dual;		# 查询dual表中的数据
```



实例是数据库的一个后台进程



```sql
# 如果可以登录任意的一个用户可以通过一下方法来知道当前有哪些用户
select distinct owner from all_objects # 查看当前用户
```

- oracle 查看当前用户名
  `show user`
  `select user from dual`
- oracle 查看所有用户名
  `select * from all_users`



## 表设计



## 约束





values ('bc04e29c0fd04be6a7087284334ef3b1', '64eb83e9545c4fcfa181d9c99268f4db', '8370', '2', '1', '116.04972222222223', '301', '350', '356.576721', '飞机编队', 'f4a9aedd-1ef4-45ca-ae29-bb90fae524f3', '未知', '1', '1', '未知天气', '2025/07/02 01:35:51', '60094', 'f4a9aedd-1ef4-45ca-ae29-bb90fae524f3', '白方', 'f4a9aedd-1ef4-45ca-ae29-bb90fae524f3', '17.74000000000001');
insert into TS_MARKTOOLS_GROUPTARGET (dataidid, disknum, groupid, attribute, armtype, longitude, height, speed, course, name, type, task, combineflag, objnum, weather, wartime, actualtime, property, views, members, latitude)



# 文献阅读

### 轨迹聚类

[1]王世辉,祝永新,汪辉等.融合运动轨迹特征的多模态群体行为识别方法[J].微电子学与计算机,2021,38(11):7-13.DOI:10.19304/J.ISSN1000-7180.2021.0341.

https://kns.cnki.net/KXReader/Detail?invoice=jEILzj%2Ff%2FjDedkUku5peU%2FOb5SCGv4JXmNjlndcmTIiuDDg1p95nzjKBvg%2FDCE7FghG5E98NtcGfuDPzRVwJz6JuH%2FnwTrSweMf0RqwRYB6d4%2BWzfCBz7fjPPMqp7HXICmLGtfojjBWwTj32DalJ7%2Fh1cGa545KmAEnc%2BlMV3NU%3D&DBCODE=CJFD&FileName=WXYJ202111002&TABLEName=cjfdlast2021&nonce=22E17CC9DEBF4550936F4E6D7506DDF5&uid=&TIMESTAMP=1678424642813

计算机兵棋作战实体轨迹聚类算法

https://kns.cnki.net/kcms2/article/abstract?v=3uoqIhG8C44YLTlOAiTRKgchrJ08w1e7xAZywCwkEEKIMEv2UBdFuHSD7ZKUS9Ye5namngcM7FQFOZwNHR-HBCglP6drbw97&uniplatform=NZKPT



目前基于LSTM的群体行为识别无法充分挖掘个体间在群体层面时空特征的问题，提出一种基于LSTM-Transformer的群体-个体时空特征融合群体行为识别模型。



## 轨迹聚类

[2]万宜春,陈志龙,何昌其等.基于时空和作战编组的兵棋推演系统**轨迹聚类算法**[J].指挥控制与仿真,2023,45(01):108-118.

https://kns.cnki.net/kcms2/article/abstract?v=3uoqIhG8C44YLTlOAiTRKibYlV5Vjs7ioT0BO4yQ4m_mOgeS2ml3UE_FPa9d0ApOiAkzC0UWIic-Qg0gxbWyGsMVIyh3iyxA&uniplatform=NZKPT

该算法分为轨迹压缩、相似性度量、轨迹线段聚类和可视化4个部分

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230310132206036.png" alt="image-20230310132206036" style="zoom:33%;" />



相似性度量：空间、时间、编队、轨迹相似度

轨迹线段聚类：使用DPC聚类算法

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230310134308787.png" alt="image-20230310134308787" style="zoom:33%;" />





<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230310132936759.png" alt="image-20230310132936759" style="zoom:33%;" />

从CTUW算法的轨迹聚类效果来看，能够实现轨迹线段的聚类，并且在可视化表现上能够为代表轨迹赋予关联棋子总称和时间信息，能够支持机动态势的动态展示。







## 数据处理

使用navicat 15打开sql文件并转为csv文件，再使用python处理csv文件中的数据

Pandas 是 Python 语言的一个扩展程序库，用于数据分析。

标注好的数据

![image-20230324132223957](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230324132223957.png)

点集数据

![image-20230324132256350](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230324132256350.png)



## 实例分割

语义分割是对图像中的每个像素划分出对应的类别,实现像素级别的分类.根据图1(a)需要划分的类别标签,在图1(b)中,将图中的“瓶子”、“杯子”、“立方体”实现像素级别的分类.

实例分割实在语义分割的基础上，进一步分割已划分类别的具体对象，即分割出实例。实例分割与语义分割的不同之处在于,不仅要进行像素级别的分类,还需在具体类别基础上区分出不同个体.这也对分割算法提出了更高的要求.如图1(c)所示,在语义分割的基础之上不仅要分割出“瓶子”和“杯子”两个类,还要用不同的颜色区分同属一类的不同“立方体”实例。

![image-20230324112721436](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230324112721436.png)

实例分割（Instance Segmentation）既具备语义分割（Semantic Segmentation）的特点，需要做到**像素层面上的分类**，也具备目标检测（Object Detection）的一部分特点，即**需要定位出不同实例，即使它们是同一种类**。

实例分割的研究有两条线

**自上而下的实例分割方法**

思路是：首先通过目标检测的方法**找出实例所在的区域**（bounding box），再**在检测框内进行语义分割**，每个分割结果都作为一个不同的实例输出。

**自下而上的实例分割方法**

思路是：首先进行像素级别的语义分割，再通过聚类、度量学习等手段区分不同的实例。这种方法虽然保持了更好的低层特征（细节信息和位置信息）



实际上也就是先分群再分类，或者先分类再分群。与本项目相似，区别在于大部分实例分割案例是对图像作处理，而本项目是对数据点作处理。



### 基于深度学习的图像实例分割技术

![image-20230324131800050](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230324131800050.png)



![image-20230324131435779](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230324131435779.png)

目标检测

![image-20230324130901348](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230324130901348.png)
