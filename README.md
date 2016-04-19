# ARN
AuReiNand v5.1整合包--N3DS A9LH专用


该整合包里含Decrypt9 + EmuNAND9 + SafeA9LHInstaller；
这里提供的是完整包、建议删掉对应的旧版文件，复制粘贴新文件到SD卡即可。

SD卡文件目录结构说明
SD:.
│  arm9loaderhax.bin         --AuReiNand A9LH 
│  
├─aurei
│  │  firmware.bin           --10.2(NTR) FIRM；非NTR用户可以直接删掉该文件，ARN将加载CTRNAND的FIRM  
│  │  
│  └─payloads
│          def_D9.bin        --Decrypt9WIP 
│          x_SafeA9LH.bin    --SafeA9LHInstaller v1.5.2
│          y_E9.bin          --EmuNAND9 
│          
└─Decrypt9
        aeskeydb.bin         --slot0x1BKeyX, slot0x05KeyY, slot0x18keyX, slot0x25KeyX
        d9logo.bin
        seeddb.bin

如果aurei目录下没有config.bin，开机后将自动进ARN设置菜单（以后可以在启动时按住Select键进入）。

ARN设置菜单简要说明：
"Screen-init brightness: 4( ) 3( ) 2( ) 1( )",             --四级亮度调整、1是最暗，仅限noscreeninit的A9LH用户使用  
"New 3DS CPU: Off( ) L2( ) Clock( ) L2+Clock( )" };        --N3DS提升CPU的频率、开启扩展的L2 Cache，有需要的可以选 
"( ) Autoboot SysNAND",                                    --自动启动真实系统，有需要的选（保留虚拟系统的A9LH用户要开机进真实系统的也要选） 
"( ) Use SysNAND FIRM as default (A9LH-only)"              --默认使用真实系统分区的FIRM（仅限A9LH使用），有需要的可以选
"( ) Force A9LH detection",                                --强制A9LH破解侦测，一般不用选
"( ) Use second EmuNAND as default",                       --SD卡有两个虚拟系统时才用得到，一般不用选
"( ) Enable region/language emulation"                     --启用区域/语言模拟，有需要的可以选
"( ) Use developer UNITINFO",                              --启用开发者出错信息提示，一般不用选
"( ) Show current NAND in System Settings",                --在3DS系统设置里显示NAND类型，例如"Sys"表示真实系统，出于兼容性考虑一般不用选 
"( ) Show GBA boot screen in patched AGB_FIRM",            --运行GBAVC游戏时显示GBA开机画面，出于兼容性考虑一般不用选 
"( ) Enable splash screen with no screen-init" }           --noscreeninit的A9LH用户启用开机画面，一般不用选 


注：ARM9LoaderHax分screen-init和no screen-init的版本，要更新A9LH（stage1&stage2）请用SafeA9LHInstaller v1.5.2。
Screen-Init = 在A9LH被调用的瞬间初始化屏幕且开启屏幕背光（简单地说就是屏幕有显示）
Non Screen-Init = A9LH下屏幕和背光默认不打开，仅当加载Payload、设置菜单、splash等时才启用 

ARN内置启动管理器（boot loader），该整合包里的payloads使用说明：
按住Start键冷启动进入Decrypt9，按住Y键冷启动进入EmuNAND9，按住X键冷启动进入SafeA9LHInstaller。
相对常用到的是D9（备份还原、加密解密）和G9（全能文件管理器），E9（格式化工具）和SafeA9LHInstaller（A9LH破解安装更新工具）较少使用。
注意：请谨慎使用这4个应用，误操作可能导致移除A9LH破解甚至变砖！！！

ARN Loader快捷键说明：
up, down, left, right, x, y不需要按L键组合；select、r需要按L+Select或L+R组合；A、B键被ARN占用，不能再作为Loader的快捷键。
现在start键的payload文件可命名为default.bin或def_name.bin（后者可读性更佳），select键的可命名为select.bin或sel_name.bin。
其它按键的使用方法也是类似的，例如r键的payload命名为r.bin或r_name.bin都是可以的。
度盘里有Uncart9、GodMode9等A9LH原生应用，可以按上面描述改名后放在\aurei\payloads目录下使用。
  
Github项目链接：
https://github.com/AuroraWright/AuReiNand

gbatemp发布帖：
http://gbatemp.net/threads/aureinand-n3ds-o3ds-a9lh.411110/

下载地址：
http://yun.baidu.com/s/1WEvbK里的AuReiNand A9LH.zip 
老3DS的NTR用户请下载度盘里的NTRFIRMs.7z，解压缩后替换aurei目录下的FIRM文件。

度盘里SafeA9LHInstaller v1.5.2整合包含screen-init的stage1&stage2(https://github.com/AuroraWright/arm9loaderhax)，
noscreeninit 0406.7z是不带screen-init的stage1&stage2(https://github.com/AuroraWright/arm9loaderhax/tree/noscreeninit)。
noscreen-init的A9LH兼容性不如scree-init的，一般用户建议使用screen-init的A9LH。

