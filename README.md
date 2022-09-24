# SmartOnmyoji
> 虽然有很多大佬有写过类似的脚本，但其实这是个学习项目，通过这个项目基本花了一个月学会了python，这里注释虽然不完整，代码不够简洁，功能也不够丰富，但是用更加优雅的方法继续完善~

## 始于痒痒鼠，不止于痒痒鼠
> 支持所有需要自动点点点的软件 —— windows程序、安卓APP


### 安装方法
**推荐直接下载使用已编译打包的程序：https://github.com/aicezam/SmartOnmyoji/releases** 
下载压缩包解压后双击运行 **smart_onmyoji_start.exe**

或启动windows命令行终端cmd或powershell，安装python，克隆仓库，进入根目录下，安装 requirements.txt 依赖库：pywin32、opencv-python、PyQt5、PyAutoGUI
```
1. python安装（版本大于3.7.6都行）：https://www.python.org/ftp/python/3.7.6/python-3.7.6-amd64.exe
2. 克隆或下载本项目
3. 运行power shell 或 cmd 进入主目录：cd .\SmartOnmyoji\ 安装依赖库：pip install -r requirements.txt
4. 运行power shell 或 cmd ：python smart_onmyoji_start.py
```


### 使用方法
- **使用前警告：请谨慎使用辅助脚本，所有不公平游戏行为都可能被官方检测导致封号（坐标偏移量越小、点击频率越快，越容易被检测）**

1. 选择使用的客户端，推荐使用**MuMu模拟器**([官网](https://yys.163.com/zmb/))、阴阳师桌面版（[NGA论坛](https://g.nga.cn/read.php?tid=29661629)）、雷电模拟器([官网](https://www.ldmnq.com/))
2. 选择匹配目标Window或Android
3. 选择单开模式还是多开模式，初次使用建议单开
4. 点击选择窗体，在倒计时结束前点击窗体，结束后显示窗口标题
5. 选择目标名称，初次使用推荐选择 **[御魂]** 模式，在软件目录下打开 **./img/yuhun/** ,文件夹下的图片就是御魂模式需要匹配的目标
6. 调整脚本运行时间，默认即可，最好不超过三小时
7. 调整匹配间隔，默认3秒即可
8. 调整坐标偏移，可以在安全性和准确性之间权衡，默认即可
9. 选择运行模式，推荐正常模式
   + 正常模式：即后台模式(不能点击最小化，可以被其他窗口覆盖，可以正常使用鼠标)，但不支持部分窗体（如网易MuMu、网易云游戏）
   + 兼容模式：即前台模式(始终保持窗口最前，不能正常使用鼠标)，支持所有窗体
10. 调整压缩截图，设置在0.6左右时，准确率和速度能兼顾，如果对匹配速度可以忍受，不建议修改压缩率（压缩率越低，准确度越低）
11. 设置匹配方法，初次使用推荐选择特征点匹配
    + 模板匹配, 速度快，对目标图片要求一模一样
    + 特征点匹配，速度慢，对目标图片要求看起来差不多就行了
12. 选择脚本结束后操作，默认即可，字面意思
13. 若你使用桌面版客户端，请勾选**桌面版防异常**，请打开配置文件**config.ini**修改window系统屏幕缩放率，即**[other_setting]** -> **srceen_scale_rate**
14. 最后点击开始，即可运行并且输出运行日志

- 推荐使用
- 只要每天正常时间内，不刷满300次，理论上不会收到鬼使黑的信，**请按正常时间正常频率使用脚本，偶尔还是用一下樱饼，总使用脚本有被封号的风险**
- 

### 注意事项

+ 本脚本运行逻辑为，定时获取窗口的截图，依次对目标图片进行匹配，匹配成功获取到图片中心坐标点，然后随机延迟并点击附近随机坐标
+ 阴阳师电脑版使用模板匹配时，不要调分辨率，如果要调分辨率，需要重新截图，然后放到/img目录的对应文件夹下面
+ 如果发现总是匹配失败，可能是/img模板图片问题，可以重新截图，或使用特征点匹配方法，或切换为 **兼容模式** ，也可自行调试代码看截图是否成功，找看看是哪儿的问题
+ 特征点匹配方法适用窗体中没有多个相同的待检测目标，而且待检测目标与周围差异比较大，否则会不准确
+ 支持安卓手机，需用USB连上电脑，并打开手机调试模式，使用 安卓-ADB 模式时，可以使用特征点匹配方式，不过有点慢，要不就重新截图替换/img目录下的全部图片
+ 支持游戏多开，仅需要运行1个脚本，需勾选多开并点击“选择窗体”，以获取窗口句柄编号，每个编号将对应一个窗口（可能不支持模拟器多开，未测试）
+ 不想使用cmd编译的，可以自行编译为win程序，编译后需要把img文件夹和modules文件夹放进根目录中，手动编译可使用：pyinstaller --distpath Release/ -w -i logo.ico --clean .\smart_onmyoji_start.py
+ 除了阴阳师，也可以其他点点点的游戏
+ **img/huntu/**图片集是转为挖土而制作的目标集，为本人运行8W体力逐步优化精选目标图片
+ 由于图片匹配是依次的，在图片前缀命名不同的数字即可设置点击的优先级，具体可参考./img/huntu图片集
+ 可设置匹配间隔为0.6秒，可媲美人手点击速度，（由于匹配频率不为点击频率，故匹配频率过快理论上不会收到鬼使黑的信），挖土有奇效
+ 只要每天正常时间内，不刷满300次，理论上也不会收到鬼使黑的信，**请按正常时间正常频率使用脚本，偶尔还是用一下樱饼，总使用脚本有被封号的风险**


### 功能预览

- UI界面、可配置参数：可修改执行时间、间隔时间、匹配方式、压缩率、执行完成后的操作等

![image](https://user-images.githubusercontent.com/39365915/165800269-7ed503ed-8f05-4853-bb32-91486d705694.png)



- 模板匹配方法：不能随意调整窗体分辨率，模板图片与窗体中的部分必须一致

![image](https://user-images.githubusercontent.com/39365915/158008385-6d661a3f-51a7-44c0-9b8b-b872cfed60eb.png)



- 特征点匹配方法：可以随便调整窗体分辨率，也可以对目标图片旋转、缩放，都可以匹配到

![image](https://user-images.githubusercontent.com/39365915/158009257-97dbc188-aa5a-4eb6-a559-03cae7e0a5d1.png)


### 已知BUG
1. ~~如果运行过长时间（5小时以上），会有明显卡顿现象（连续肝了3天绘卷，消耗了5w体力）~~ 已修复
2. 如果电脑不能播放声音（比如设为静音），可能会停止运行（win10），可以在配置文件关闭“警告提示音”来解决


### 已实现功能
- [x] 支持abd模式，电脑连手机自动截图
- [x] 支持切换选择匹配模式，特征点匹配（自适应分辨率，不用重新截图，但速度略慢，且不太准确）、模板匹配（速度更快，更精确，但麻烦，不能改分辨率）
- [x] 加载图片时记录所有图片的特征信息，优化识别速度
- [x] 支持压缩图片以提升脚本识别速度，默认为1不压缩
- [x] 所有图片转灰度图，并保存在内存里，识别速度快多了
- [x] 修复中文路径报错的问题
- [x] 兼容所有windows窗体的截图和点击
- [x] 使用QT5重构UI界面
- [x] 增加选择自定义匹配图片文件夹的功能
- [x] 支持多开，多开可选择多个游戏窗口，将自动对多个窗口截图、找图、点击
- [x] 界面参数缓存，每次启动会加载上次使用的参数（可通过修改配置文件关闭此功能）
- [ ] ~~优化百鬼夜行的选式神和砸豆子逻辑（yolov5），尝试跑了个模型，但是效果不好，会导致程序特别臃肿，而且运行速度特别慢~~ 
- [ ] ~~增加御灵、地域鬼王、逢魔、秘闻副本等默认场景，现支持自定义，可通过修改配置文件自定义场景~~
- [x] 兼容常用安卓模拟器后台点击
- [x] 支持手机端局域网内远程使用（不用在手机安装app），配置文件配置局域网IP即可
- [x] 增加真实点击模拟，混淆坐标点击轨迹（20%的几率触发）

### 更新记录

- 2022年9月24日 可自定义设置混淆额外点击的触发概率
- 2022年9月22日 增加快捷打开“配置文件、img文件夹”的功能
- 2022年9月21日 修复长时间运行导致匹配速度变慢的[bug](https://github.com/aicezam/SmartOnmyoji/issues/22)（日志过多）
- 2022年9月06日 修复Window系统分辨率导致的失真[bug](https://github.com/aicezam/SmartOnmyoji/issues/8),优化匹配时间间隔达到设定值
- 2022年8月11日 优化时间计算算法（之前根据次数计算，会因为设备性能原因导致计算不准确，现在说多久完成就多久，不再拖延）
- 2022年8月05日 配置文件增加注释说明，增加混淆坐标点击的开关，配置文件中设为False后关闭该功能（小窗口容易点到其他地方，使匹配目标被遮挡导致识别失败）
- 2022年7月07日 增加真实点击模拟，混淆坐标点击（怀疑痒痒鼠后台会记录坐标点击轨迹数据，如果太规律容易被ban号）
- 2022年6月07日 模拟器兼容方法优化，修复可能存在的兼容点击失败问题
- 2022年5月22日 兼容常见模拟器：雷电模拟器、MuMu模拟器、夜神模拟器、腾讯手游助手、逍遥模拟器后台点击，只测试了前面2个~
- 2022年5月09日 修复不能识别雷神模拟器的bug，另外增加部分异常情况的提示音（不喜欢可以通过配置文件关闭）
- 2022年5月07日 添加免责声明，优化运行日志显示
- 2022年5月04日 每次使用脚本时，参数会被记录在 config.ini 文件中，下次启动时会加载上次使用的参数，配置文件中也有其他配置，可修改以实现不同的需要
- 2022年4月30日 优化多开功能，仅需要运行1个脚本，需勾选多开并点击“选择窗体”，以获取窗口句柄编号，每个编号将对应一个窗口
- 2022年4月29日 更新支持多开方法（运行多个脚本，每个脚本对应一个窗口），兼容png格式的模板截图~
- 2022年4月26日 调整部分默认参数，更新雷电模拟器后台点击方法（感谢 @zyhazwraith https://github.com/zyhazwraith 提供的思路 https://github.com/aicezam/SmartOnmyoji/issues/7 ）
- 2022年4月07日 更新防检测异常的逻辑（虽然可能没什么用）
- 2022年4月03日 增加选择自定义匹配目标图片文件夹的功能
- 2022年4月02日 修复bug：停止匹配后，偶尔会触发继续匹配运行的bug
- 2022年3月31日 移除重复的依赖，运行时检测是否使用管理员身份运行，脚本默认包含adb程序，为代码增加部分注释
- 2022年3月25日 使用PYQT5重构GUI，使用pyautogui替换pymouse库
- 2022年3月12日 增加兼容模式，支持在所有的 windows窗体 截图和点击，包括模拟器、云游戏、scrcpy 等， 兼容模式下 **窗体会自动置顶，不再支持后台点击**
- 2022年3月10日 增加鼠标点击选择窗体的功能，（窗口标题名称 - 下拉选择 “开始后鼠标点击选择窗体”，5秒内点击要匹配窗体）
- 2022年1月27日 修复opencv在中文路径下报错的问题
- 2022年1月26日 重新加入模板匹配方法，并设为默认方法，因为发现匹配速度有点慢，准确率不太高
- 2022年1月19日 优化匹配速度，截图和读取模板图片时先转灰度，支持对截图设置压缩率，进一步优化匹配速度；更换全部匹配方法为sift匹配；增加对安卓设备的支持，通过ADB实现；
- 2022年1月15日 首次提交，自动截图、匹配、点击

### 其他说明
仅作学习用途，请勿用于其他非法途径！
