# CrosSCLR





## 数据集

NTU-RGB+D数据集介绍

GitHub：https://github.com/shahroudy/NTURGB-D

https://blog.csdn.net/weixin_51450749/article/details/111768242

画某一帧：https://blog.csdn.net/qq_43601378/article/details/120655378

画动画：https://blog.csdn.net/weixin_43863869/article/details/121713885



## 对比学习



怎样找正样本和负样本



## ST-GCN

交通

论文解读博客

https://blog.csdn.net/weixin_44065323/article/details/135827620



骨架



https://www.zhihu.com/question/276101856

代码

```
config/st_gcn: 配置文件
	ntu-xview: 处理ntu-xview数据的配置文件
data: 数据存放
feeder: 
models: 
net: 
processor: 
	demo*.py: 			和video相关，视频识别出骨架等
	io.py: 				感觉和数据进出GPU有关
	processor.py: 		有写日志的代码，展示epoch信息。解析args，如work_dir，epoch数，GPU相关设置，						  日志，模型等
	recognition.py: 	有写日志的代码，展示TopK等。解析args，如lr学习率、step步数、optimizer							优化器等
		Class REC_Processor(): 	骨架识别入口（之前的工作是通过视频获得骨架数据，从这里开始就是骨架识别									了）
tools: 
torchlight: 
	io.py: 有写日志的代码，时间信息，输出路径信息。里面import_class函数用来调用自己本地写的类。
work_dir: 
main.py
```



| ------------------------------------------------------------ |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| config/st_gcn                                                | 配置文件                                                     |
| ntu-xview                                                    | 处理ntu-xview数据的配置文件                                  |
| data                                                         | 数据存放                                                     |
| feeder                                                       |                                                              |
|                                                              |                                                              |
| net                                                          |                                                              |
|                                                              |                                                              |
| processor                                                    |                                                              |
| demo[].py                                                    | 和video相关，视频识别出骨架等                                |
| io.py                                                        | 感觉和数据进出GPU有关                                        |
| processor.py                                                 | 有写日志的代码，展示epoch信息。画图时可以注释掉evaluation里的self.test() //用来输出mean loss的<br />解析args，如work_dir，epoch数，GPU相关设置，日志，模型等 |
| recognition.py                                               | 调用日志的代码解析args，如lr学习率、step步数、optimizer优化器 |
| Class REC_Processor()                                        | 骨架识别入口（之前的工作是通过视频获得骨架数据，从这里开始就是骨架识别了 |
|                                                              |                                                              |
| tools                                                        |                                                              |
|                                                              |                                                              |
| torchlight                                                   |                                                              |
| io.py                                                        | 有写日志的代码，时间信息，输出路径信息。里面import_class函数用来调用自己本地写的类。 |
|                                                              |                                                              |
| main.py                                                      |                                                              |