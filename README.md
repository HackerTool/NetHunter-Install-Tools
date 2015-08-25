## 说明

写这脚本最初的原因是NetHunter官网的Windows版本工具刷入的系统导致Android没法自动更新。</br>
此脚本没有使用修改版的内核(Modified_Boot)和关闭强制加密内核(NoForce_Encrypt_Kernel)，需要使用的话可以使用More里的ADB CMD手动刷。</br>
Recovery使用的是官方的版本，TWRP版本的Recovery只是临时加载，并不写入。</br>
使用此脚本刷的设备可以使用Android的自动更新(大概)我测试的时候更新到一半提示失败(我猜应该是Google的服务应用没更新导致的)</br>
我只有一部设备，还是日常使用的，测试时已经刷了6-7次了，毕竟刷多了对设备不会有好处的，所以不是所有的功能都测试过。</br>

## 使用

此脚本使用ADB调试工具作为功能实现，所以系统必须支持adb运行。</br>
64位系统可能需要安装 `lib32gcc1` `lib32stdc++6` `libc6-i386` 几个依赖包</br>
如果使用的是Kali Linux直接使用 `apt-gat install -y google-nexus-tools` 会自动安装依赖包</br>
另外要确认系统已经安装 `wget` `tar`</br>

打开开发者模式
1. 设置 > 关于手机 > 版本号(连续点5下再返回) > 开发者选项 > 打开USB调试</br>
2. 用数据线连接电脑，执行脚本，勾选"始终允许从这台计算机"，点击确定</br>

然后按照脚本里的提升输入指定的编号开始操作，必须在脚本的所在目录执行，不能在其他目录里执行</br>

正常刷NetHunter的步骤：</br>
1. 运行 ./nethunter-linux.sh</br>
2. 输入 1 解锁设备</br>
3. 输入 3 刷 Android 系统</br>
4. 输入 2 进行Root</br>
5. 输入 4 刷 NetHunter</br>

更多的功能在 5 More 里可以找到</br>

## 可能遇到的问题

如果文件不能自动下载，请手动下载，然后复制到 `images` 文件夹里，注释掉那一行代码</br>
如果脚本执行不动，感觉卡住了，请不要终止运行，这可能是 `adb` 在 `push` 文件到SD卡里，刷NetHunter的时候会遇见</br>
如果设备是 `32GB` 的，输入Android后系统显示只有 `16GB` 了，请在设备上恢复出厂设置</br>
如果操作错误导致设备卡在某个界面，可以长按电源键。开机按住两颗音量键+电源键可以启动到 `Fastboot` 模式(Nexus 5)</br>
