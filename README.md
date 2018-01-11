因为我自己用deskmini，就动手改了7.2版的bios（支持Cfl处理器和核显），
已刷机测试可以正常启动进系统（我用的是i3-7100，吧友用8100也测试过了），如有风险请自行承担。
https://pan.baidu.com/s/1c2JHlc8

操作流程简述：

如果你的bios是7.20或7.20以下，请先升级至7.20版，备份好自己的BIOS设置后恢复出厂设置；
再用AFUWIN备份主板的BIOS region，接着用MMTool或UEFITool打开添加CFL处理器微码，替换1073版GOP、1054版VBIOS后保存ROM；
然后用AFUWIN刷修改后的ROM即可，这样是相当安全的操作（只动到BIOS region）。

如果你的bios是7.30版还需要解锁me region，7.30版的ME是11.8.50.3425不支持在100系主板上用CFL处理器，据说微码识别CFL后ME会自动断电关机，
而7.20版的ME固件是11.6.0.1126就不会有上面的问题。
BIOS 7.30版的请先解锁ME降级，详细见wiki--04 ME unlock降级。


具体操作步骤：

A）用MMTool修改处理器微码，详细见wiki--02 修改处理器微码，添加对CFL处理器的支持

B）按wiki--03 合成新版VBIOS来生成1054版的VBIOS，另存为vbios1054.bin

C）用UEFITool_0.22.1打开H11STXC7.20mod.rom，Ctrl+F搜索GUID（380B6B4F-1454-41F2-A6D3-61D1333E8CB4）即GOP模块，
   找到后选中，右键Replace body…选择Intel Skl-Kbl-Cfl GOP 9.0.1073.bin（网盘里有分享）替换；
   接着Ctrl+F搜索GUID（C5A4306E-E247-4ECD-A9D8-5B1985D3DCDA）即VBIOS模块，
   找到后选中，右键Replace body…选择刚才的vbios1054.bin替换，保存H11STXC7.20mod.rom
   
至此完成H110主板对Cfl处理器的识别、核显支持的BIOS修改操作。

接着用AFUWIN刷修改好的BIOS，AFUWIN里不要选自动重启、万一操作出错还能补救；

如果用InstantFlash刷修改的ROM，需要先用UBU 1.6工具运行UBU.bat自动去除安全校验模块才可以。




