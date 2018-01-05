因为我自己用deskmini，就动手改了7.2版的bios（支持Cfl处理器和核显），
已刷机测试可以正常启动进系统（上的是i3-7100，手头没有8100），如有风险请自行承担。
https://pan.baidu.com/s/1c2JHlc8

操作流程简述：
如果你的bios是7.20或7.20以下，请先升级至7.20版，备份好自己的BIOS设置后恢复出厂设置；
再用AFUWIN备份主板的BIOS region，接着用MMTool或UEFITool添加CFL处理器微码，替换1073版GOP、1054版VBIOS后保存ROM；
然后用AFUWIN刷修改后的ROM即可，这样是相当安全的操作。

如果你的bios是7.30版，额外需要解锁me region，7.30版的ME是11.8.50.3425可能不支持在100/200系主板用CFL处理器在微码识别后ME断电关机，
7.20版的ME是11.6.0.1126不会有上面的问题。
7.30版的操作步骤跟7.20版是一样的，只是后面还需要人工解锁ME region，再从7.20版BIOS提取旧版ME用Intel FPT等工具导入。


具体操作步骤：
A）下载同品牌Z370主板的BIOS，用MMTool_5.07打开并提取Cfl处理器的微码—06EB
CPU Patch->Patch file输出文件名06EB.bin->Extract a Patch Data->Apply
UEFITool

B）下载deskmini的BIOS 7.20版。用MMTool_5.07打开bios rom，在CPU Patch选中06E3微码->Delete a Patch Data->Apply删除对Skl处理器的支持（腾出空间），再插入刚才导出的06EB.bin添加对Cfl处理器的支持（Insert a Patch Data->Apply）；另存为H11STXC7.20mod.rom

C）用UEFITool_0.22.1打开deskmini的原版bios H11STXC7.20.rom，ctrl+f->GUID搜索VBIOS模块（C5A4306E-E247-4ECD-A9D8-5B1985D3DCDA），右键选择extract body...保存为vbios1039.bin （这里版本号可用WinHex打开查看）

D）用BMP（Intel® Binary Modification Program）打开vbios1039.bin（二进制数据）和skl_1039.bsf（对应的脚本，从VBIOS_and_BSF.7z中提取），按Menu -> "BIOS Setting -> Save All" -> 'transfer.ssf'操作另存为transfer.ssf

E）用文本编辑器打开（例如EmEditor）打开transfer.ssf，找到“STRING $Signon Intel(R) SKL/KBL Mobile/Desktop PCI Accelerated SVGA BIOS\r\nBuild Number: 1039 PC 14.34  03/18/2016  02:56:01\r\nDECOMPILATION OR DISASSEMBLY PROHIBITED\r\n”这一行并删除，保存

F）用BMP打开skl_1054.dat和skl_1054.bsf（从VBIOS_and_BSF.7z中提取），按Menu -> "BIOS Setting -> Apply All" -> 'transfer.ssf' and save, example 'vbios_new.dat'操作用之前的transfer.ssf合并覆盖，另存为vbios1054.bin

G）用UEFITool_0.22.1打开H11STXC7.20mod.rom，ctrl+f搜索GOP模块（380B6B4F-1454-41F2-A6D3-61D1333E8CB4）和VBIOS模块（C5A4306E-E247-4ECD-A9D8-5B1985D3DCDA），右键Replace body…分别选择Intel Skl-Kbl-Cfl GOP 9.0.1073.bin（网盘里有分享）替换、选择vbios1054.bin替换后，保存H11STXC7.20mod.rom

至此完成H110主板对Cfl处理器的识别、核显支持的BIOS修改操作。
因为BIOS空间有限，只能存放两个处理器微码，修改后的BIOS只支持Kbl7代和Cfl8代、不支持Skl6代。
先将deskmini的bios更新到官方7.20版，再用网盘里的AfuWin刷修改后的bios（同版本）。



