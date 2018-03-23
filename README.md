操作流程简述：

    Plan A
    用UBU去除修改版BIOS的安全校验，接着解锁ME确认后，再用InstantFlash刷修改好的7.20 BIOS应该是最快最简单的方法。
    该方法已由吧友测试通过，降级ME和修改BIOS一步到位。

    Plan B
    还是不放心的话，解锁ME确认后，再用InstantFlash刷官方7.20 BIOS，重启确认ME降级是否成功；
    接着按7.20版的教程刷修改好的7.20 BIOS也可以。


补充：
已确认，从gop 9.0.1040 & vbios 9.0.1034开始支持kabylake；

通过几款Z370的初版bios解析，猜测从gop 9.0.1068 & vbios 9.0.1054开始支持coffeelake，但Z370 vbios的平台还是skl/kbl；

而最新的H310和B360的vbios是真正cfl平台的。

2018-3-23更新，目前H110上i7 8700等必须先关闭超线程，i5 8400或8500不需要，pin mod都是必需的。
一般来说H110配8100是最方便也是可靠性最高的，搭配i5 6核需要硬改有一定风险，搭配i7的话不建议。

另据贴吧大佬消息，ME11.6是不用改主板SKU的，ME11.7的话需要用Flash Image Tool改主板SKU、
并且还需导出主板ME参数合成新版ME替换后再生成新的bios rom。

如果是Z170或Z270，可以考虑移植同品牌主板Z370的bios：
简单流程是用Intel Flash Image Tool解包主板原始bios，

然后提取vbios并按教程导出参数合成1054版，

接着用FIT修改主板SKU为Z370，

然后用Z370的bios region替换原始的bios region，记得用上面修改好的vbios 1054替换Z370的vbios，

最后FIT生成新镜像，用编程器刷入（注意Flash芯片容量大小要匹配）。

当然pin mod还是需要的，好处是这样修改后不用再考虑ME版本，坏处是可能会有些兼容问题等。


