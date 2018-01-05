因为我自己用deskmini，就动手改了7.2版的bios（支持Cfl处理器和核显），
已刷机测试可以正常启动进系统（上的是i3-7100，手头没有8100），如有风险请自行承担。
https://pan.baidu.com/s/1c2JHlc8

操作流程简述：
如果你的bios是7.20或7.20以下，请先升级至7.20版，备份好自己的BIOS设置后恢复出厂设置；
再用AFUWIN备份主板的BIOS region，接着用MMTool或UEFITool打开添加CFL处理器微码，替换1073版GOP、1054版VBIOS后保存ROM；
然后用AFUWIN刷修改后的ROM即可，这样是相当安全的操作（只动到BIOS region）。

如果你的bios是7.30版，额外需要解锁me region，7.30版的ME是11.8.50.3425，可能不支持在100/200系主板用CFL处理器、据说微码识别后ME断电关机，
7.20版的ME是11.6.0.1126不会有上面的问题。
7.30版的操作步骤前面跟7.20版是一样的，只是后面还需要人工解锁ME region，再从7.20版BIOS提取旧版ME用Intel FPT等工具导入。


具体操作步骤：

A）用MMTool修改处理器微码，详细见wiki--修改处理器微码，添加对CFL处理器的支持

B）按wiki--合成新版VBIOS来生成1054版的VBIOS，另存为vbios1054.bin

C）用UEFITool_0.22.1打开H11STXC7.20mod.rom，Ctrl+F搜索GUID（380B6B4F-1454-41F2-A6D3-61D1333E8CB4）即GOP模块，
   找到后选中，右键Replace body…选择Intel Skl-Kbl-Cfl GOP 9.0.1073.bin（网盘里有分享）替换；
   接着Ctrl+F搜索GUID（C5A4306E-E247-4ECD-A9D8-5B1985D3DCDA）即VBIOS模块，
   找到后选中，右键Replace body…选择刚才的vbios1054.bin替换，保存H11STXC7.20mod.rom
   
D）如果是7.30版BIOS，需要解锁ME region，降级ME FW，详细见wiki--   

至此完成H110主板对Cfl处理器的识别、核显支持的BIOS修改操作。




