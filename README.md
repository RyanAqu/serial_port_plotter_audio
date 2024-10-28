# **串口示波器简易实施**
项目参考：CieNTi / serial_port_plotter

开发环境：qt5.12.1+安装选择组件MinGW 7.3.0 64-bit（qt和tools均勾选）；打包工具为qt5.12.1（MinGW 7.3.0 64-bit）；

打包过程：①release文件夹下exe复制到任意空文件夹②qt5.12.1（MinGW 7.3.0 64-bit）命令行打开，cd到exe所在文件夹③命令行输入windeployqt xxxx.exe，完成打包

### **软件界面**
![image](https://github.com/user-attachments/assets/4e7596ee-893e-40a3-b3f3-4cdd0ee106e2)

### **软件功能**
**数据采集功能：**
1)	能够搜索、识别、调用串口接口，能根据接收站配置相应的串口参数，与接收站的串口连接，实现上位机与接收站的通信； 
2)	实现了与接收站之间的数据解析，能识别特定的起始符，对满足解析格式的数据进行实时采集，且串口速率能支撑接收站的数据率；
3)	能够实时展示解析前后的数据，将数据显示在文本区；

**数据存储与管理：**
1)	实现了数据的采集存储，开辟了磁盘空间，将所有采集到的数据存储于软件根目录下的data文件夹下，每32000个数据存储于一个txt；
2)	存储文件txt的名称根据“年月日_时分秒_data_x”的格式命名，便于定位有价值的数据，数据文件夹需要及时清理，数据存储格式便于后续的数据处理；

**数据处理与可视化：**
1)	实现了解析出的实时数据的可视化处理。用户可以通过可视化界面，对波形进行实时观察，可视化界面支持缩放、移动、清除等基础功能；
2)	实现了音频缓存、音频处理和音频播放功能，可以将解析数据转为音频数据，当缓存到32000（10s）个数据时进行播放；
3)	支持对已存数据的音频播放，在没有接收数据的情况下，可以播放已经存储在data文件夹下的数据；

### **串口输入语法**
```
/* Example: Plot two values */
printf ("$%d %d;", data1, data2);
```
