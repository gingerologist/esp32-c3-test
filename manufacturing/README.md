# PCB生产文件说明

生产文件使用KiCAD生成，设置依据嘉力创的说明，其中文件名使用Protel命名规则。

https://support.jlcpcb.com/article/149-how-to-generate-gerber-and-drill-files-in-kicad



PCB尺寸40mm x 40mm，双面，厚度1.0mm，最小过孔0.4mm/0.6mm，单面摆件（正面），背面无丝印；绿色板白色丝印。



| 文件名                          | 内容                     |
| ------------------------------ | ------------------------ |
| esp32-c3-test-F_Cu.gtl         | 正面铜箔                 |
| esp32-c3-test-F_Mask.gts       | 正面阻焊                 |
| esp32-c3-test-F_Paste.gtp      | 正面锡膏（不用）         |
| esp32-c3-test-F_SilkS.gto      | 正面丝印                 |
| esp32-c3-test-B_Cu.gbl         | 背面铜箔                 |
| esp32-c3-test-B_Mask.gbs       | 背面阻焊                 |
| esp32-c3-test-Edge_Cuts.gm1    | 板框                     |
| esp32-c3-test-PTH.drl          | 金属化孔钻孔文件         |
| esp32-c3-test-PTH-drl_map.gbr  | 金属化孔钻孔图（不用）   |
| esp32-c3-test-NPTH.drl         | 非金属化孔钻孔文件       |
| esp32-c3-test-NPTH-drl_map.gbr | 非金属化孔钻孔图（不用） |



### KiCAD生成的PCB预览图

![pcb.png](/home/ma/repos/esp32-c3-test/manufacturing/pcb.png)





# BOM单与物料说明



| ref   | value               | footprint                                     | lcsc part                                                    |
| ----- | ------------------- | --------------------------------------------- | ------------------------------------------------------------ |
| C1-C3 | 10uF~22uF,16V钽电容 | EIA-35-28-21（AVX Case B），立创称CASE-B_3528 | https://item.szlcsc.com/7666.html (10uF)<br />https://item.szlcsc.com/8497.html (22uF) |
| C4    | 0.1u,10V            | 0603                                          |                                                              |
| D1-D5 | LED                 | 0805                                          | 见下面说明                                                   |
| J9    | USB micro B         | Molex 105017-0001                             | https://item.szlcsc.com/147313.html                          |
| Q1-Q5 | DTC143E兼容物料     | SOT-23                                        | https://item.szlcsc.com/14526.html                           |
| R1-R5 | 1k,5%               | 0603                                          |                                                              |
| R6-R8 | 10k,5%              | 0603                                          |                                                              |
| U1    | ESP32-C3-MINI1-1    |                                               | https://item.szlcsc.com/3013227.html                         |
| U2    | AMS1117-3.3兼容物料 | SOT-223                                       | https://item.szlcsc.com/323882.html（友台UMW）               |



### LED

LED选料可直接在立创的分类页面（https://list.szlcsc.com/catalog/528.html）上选择厂商『国星光电』和封装『0805』，从得到的结果里选择。

D1-D5分别是红色，绿色（选择普绿/黄绿），蓝色，白色，黄色（当作暖白使用）；黄色也可以贴白色。

LED是极性元件，板上有RGBCW丝印一侧为正极，如果焊接反了不会损害器件但不会亮。



### DTC143

DTC143是基极串连和基极与射级之间并连电阻的数字晶体管；其中DTC143E是R1和R2都是4.7k的版本，只要封装相同（SOT-23）的都可以替换使用。



### AM1117-3.3

常用的800mA 3.3V固定输出LDO，芯片名称不一定以AM开头，比如ti的是LM1117-3.3；封装相同（SOT-223）的都可以替换使用。



### Molex 105017-0001

这个如果缺料的话可能需要找找兼容料，韩荣应该有兼容的但是没仔细找过。



### KiCAD生成的PCBA预览图

钽电容焊接放向可以参考图片内的器件放向。

![pcba.png](/home/ma/repos/esp32-c3-test/manufacturing/pcba.png)
