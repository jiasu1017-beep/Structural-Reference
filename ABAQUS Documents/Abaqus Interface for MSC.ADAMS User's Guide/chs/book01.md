# 1 引言





本章提供 Abaqus Interface for MSC.ADAMS 的概述。涵盖以下主题：
- ["本手册包含哪些信息？" 第 1.1 节](ch01s01.md)
- ["什么是 Abaqus Interface for MSC.ADAMS？" 第 1.2 节](ch01s02.md)
- ["使用 Abaqus Interface for MSC.ADAMS 的步骤是什么？" 第 1.3 节](ch01s03.md)
- ["模态中性文件包含哪些内容？" 第 1.4 节](ch01s04.md)

Abaqus Interface for MSC.ADAMS 的安装包含在 Abaqus 产品安装中。有关安装 Abaqus 的信息，请参阅 [Abaqus 安装和许可指南](../sgb/sgb-link.md#sgb)。



# 1.1 本手册包含哪些信息？





本手册说明如何使用 Abaqus Interface for MSC.ADAMS。有关使用 MSC.ADAMS 的一般信息，请参阅 MSC.ADAMS 文档集。您可能会发现以下 MSC.ADAMS 手册特别有用：
- *使用 ADAMS/Flex*
- *使用 ADAMS/View*




# 1.2 什么是 Abaqus Interface for MSC.ADAMS？





MSC.Software 公司的 ADAMS/Flex 产品可用于在进行 MSC.ADAMS 动力学分析时考虑组件的柔性。ADAMS/Flex 依靠有限元分析代码（如 Abaqus）以 MSC.ADAMS 可用的格式提供组件的柔性信息。Abaqus Interface for MSC.ADAMS 可用于创建 MSC.ADAMS 组件的 Abaqus 模型，并将 Abaqus 结果转换为 MSC.ADAMS 模态中性（`.mnf`）文件，这是 ADAMS/Flex 所需的格式。

Abaqus Interface for MSC.ADAMS 6.12 需要由 Abaqus 6.2 或更高版本创建的结果文件。Abaqus Interface for MSC.ADAMS 创建与 ADAMS Version 10.1 及更高版本兼容的模态中性文件。如果模态中性文件中包含模态应力和应变，则需要 ADAMS Version 12 或更高版本。




# 1.3 使用 Abaqus Interface for MSC.ADAMS 的步骤是什么？





Abaqus Interface for MSC.ADAMS 的典型用法包括从单个结果文件创建不包含应力或应变的模态中性文件，需要一次 Abaqus 分析和一次 Abaqus Interface for MSC.ADAMS 步骤。以下步骤总结了 Abaqus Interface for MSC.ADAMS 的典型用法：

**使用 Abaqus Interface for MSC.ADAMS：**

1. 为 MSC.ADAMS 模型的每个柔性组件创建 Abaqus 模型。每个组件建模为 Abaqus 子结构。
2. 运行 Abaqus 分析。
3. 运行 Abaqus Interface for MSC.ADAMS 读取分析生成的结果文件，并为 MSC.ADAMS 创建模态中性（`.mnf`）文件。
4. 将模态中性文件读入 MSC.ADAMS。必须为 MSC.ADAMS 中的每个柔性部件创建一个独立的模态中性文件。

如果您希望 Abaqus Interface for MSC.ADAMS 将应力或应变转换到模态中性文件，可以修改通用步骤。在修改后的步骤中，Abaqus Interface for MSC.ADAMS 从两个结果文件创建模态中性文件，需要两次 Abaqus 分析和两次 Abaqus Interface for MSC.ADAMS 步骤。更多信息，请参阅 ["设置 Abaqus 模型以创建包含应力或应变的模态中性文件" 第 2.3 节](ch02s03.md) 和 ["执行 **adams** 命令以创建包含应力或应变的模态中性文件" 第 3.3 节](ch03s03.md)。

本手册的其余章节将详细讨论这些步骤。




# 1.4 模态中性文件包含哪些内容？





Abaqus Interface for MSC.ADAMS 将数据从一个或多个 Abaqus 结果（`.fil`）文件转换，并创建 MSC.ADAMS 模态中性（`.mnf`）文件。根据结果文件的内容和转换参数，Abaqus Interface for MSC.ADAMS 创建包含下表所示数据块的模态中性文件（参见 [表 1-1](ch01s04.md#table-datablocks)）。

**表 1-1** 模态中性文件内容。
| 块编号 | 内容 | 由 Abaqus Interface for MSC.ADAMS 创建 |
| --- | --- | --- |
| ` 1` | 版本代码 | 是 |
| ` 2` | 标题 | 是 |
| ` 3` | 内容摘要 | 是 |
| ` 4` | 节点坐标 | 是 |
| ` 5` | <未使用> | N/A |
| ` 6` | 全局质量属性 | 是 |
| ` 7` | 特征值 | 是 |
| ` 8` | 振型 | 是 |
| ` 9` | 节点质量 | 是 |
| `10` | 节点惯性 | 是 |
| `11` | 单位 | 是 |
| `12` | 广义刚度矩阵 | 是 |
| `13` | 广义质量矩阵 | 是 |
| `14` | 单元面 | 是 |
| `15` | 广义阻尼 | 否 |
| `16` | 振型转换 | 是 |
| `17` | 界面节点 | 是 |
| `18` | 模态应力 | 可选 |
| `19` 至 `26` | 惯性不变量 | 是 |
| `27` | 模态预载荷 | 是 |
| `28` | 模态载荷 | 否 |
| `29` | 模态应变 | 可选 |





# Abaqus Interface for MSC.ADAMS 用户手册






[商标和法律声明](../popups/usb-lgl.md)

[转换表、常量和材料属性](../popups/usb-tbl.md)
<hksaddresses><officeheading><officeentry><officecountry>SIMULIA 全球总部</officecountry><officenameandcontact><officeaddress>Rising Sun Mills</officeaddress><officeaddress>166 Valley Street</officeaddress><officelocale>Providence, RI</officelocale><officezip>02909–2499</officezip><officephone> +1 401 276 4400</officephone><officefax> +1 401 276 4408</officefax><officeemail>simulia.support@3ds.com</officeemail><officeweb>http://www.3ds.com/simulia</officeweb></officenameandcontact></officeentry><officeentry><officecountry>SIMULIA 欧洲总部</officecountry><officenameandcontact><officeaddress>Stationsplein 8-K</officeaddress><officezip>6221 BT</officezip><officelocale>Maastricht</officelocale><altofficecountry>The Netherlands</altofficecountry><officephone> +31 43 7999 084</officephone><officefax> +31 43 7999 306</officefax><officeemail>simulia.europe.info@3ds.com</officeemail></officenameandcontact></officeheading></hksaddresses>
Dassault Systèmes 仿真卓越中心

| 美国 | |
| --- | --- |
| Fremont, CA | West Lafayette, IN |
| Northville, MI | Woodbury, MN |
| Beachwood, OH | Mason, OH |
| Warwick, RI | Lewisville, TX |

| 全球 | |
| --- | --- |
| 澳大利亚 | 奥地利 |
| 比荷卢 | 加拿大 |
| 中国（北京）| 中国（上海）|
| 芬兰 | 法国 |
| 德国（亚琛）| 德国（慕尼黑）|
| 印度 | 意大利 |
| 日本（大阪）| 日本（东京）|
| 韩国 | 拉丁美洲 |
| 北欧 | 英国 |

授权支持中心

| 阿根廷 | 巴西 |
| --- | --- |
| 捷克和斯洛伐克共和国 | 希腊 |
| 以色列 | 马来西亚 |
| 墨西哥 | 新西兰 |
| 波兰 | 俄罗斯、白俄罗斯和乌克兰 |
| 新加坡 | 南非 |
| 西班牙和葡萄牙 | 台湾 |
| 泰国 | 土耳其 |

<officeheading><officeentry><officecountry>美国</officecountry><officenameandcontact><officeaddress>39221 Paseo Padre Parkway, Suite F</officeaddress><officelocale>Fremont, CA</officelocale><officezip>94538-1606</officezip><officephone> +1 510 794 5891</officephone><officefax> +1 510 405 8902</officefax><officeemail>simulia.west.support@3ds.com</officeemail></officenameandcontact><officenameandcontact><officeaddress>1440 Innovation Place</officeaddress><officelocale>West Lafayette, IN</officelocale><officezip>47906-1000</officezip><officephone> +1 765 497 1373</officephone><officefax> +1 765 497 4444</officefax><officeemail>simulia.central.support@3ds.com</officeemail></officenameandcontact><officenameandcontact><officeaddress>3200 Greenfield Road</officeaddress><officeaddress>Suite 310</officeaddress><officelocale>Dearborn, MI</officelocale><officezip>48120</officezip><officephone> +1 313 827 5500</officephone><officeemail>simulia.greatlakes.info@3ds.com</officeemail></officenameandcontact><officenameandcontact><officeaddress>539 Bielenberg Drive, Suite 110</officeaddress><officelocale>Woodbury, MN</officelocale><officezip>55125</officezip><officephone> +1 612 424 9044</officephone><officefax> +1 612 424 9045</officefax><officeemail>simulia.central.support@3ds.com</officeemail></officenameandcontact><officenameandcontact><officeaddress>6105 Parkland Blvd., Suite 100</officeaddress><officelocale>Mayfield Heights, OH</officelocale><officezip>44124</officezip><officephone> +1 216 378 1070</officephone><officefax> +1 216 378 1072</officefax><officeemail>simulia.erie.info@3ds.com</officeemail></officenameandcontact><officenameandcontact><officeaddress>5181 Natorp Boulevard, Suite 205</officeaddress><officelocale>Mason, OH</officelocale><officezip>45040</officezip><officephone> +1 513 275 1430</officephone><officefax> +1 513 275 1440</officefax><officeemail>simulia.central.support@3ds.com</officeemail></officenameandcontact><officenameandcontact><officeaddress>Summit Executive Park, West Building</officeaddress><officeaddress>300 Centerville Road, Suite 209W</officeaddress><officelocale>Warwick, RI</officelocale><officezip>02886-0201</officezip><officephone> +1 401 739 3637</officephone><officefax> +1 401 739 3302</officefax><officeemail>simulia.east.support@3ds.com</officeemail></officenameandcontact><officenameandcontact><officeaddress>190 Civic Circle, Suite 210</officeaddress><officelocale>Lewisville, TX</officelocale><officezip>75067</officezip><officephone> +1 972 221 6500</officephone><officefax> +1 972 221 6550</officefax><officeemail>simulia.south.info@3ds.com</officeemail></officenameandcontact></officeentry><officeentry><officecountry>澳大利亚</officecountry><officenameandcontact><officeaddress>Ground Floor</officeaddress><officeaddress>236A Lennox Street</officeaddress><officelocale>Richmond VIC</officelocale><officezip>3121</officezip><officephone> +61 3 9421 2900</officephone><officefax> +61 3 9429 7640</officefax><officeemail>simulia.au.support@3ds.com</officeemail></officenameandcontact></officeentry><officeentry><officecountry>奥地利</officecountry><officenameandcontact><officeaddress>Wienerbergstrasse 51</officeaddress><officezip>A-1120</officezip><officelocale>Vienna</officelocale><officephone> +43 1 22 707 200</officephone><officefax> +43 1 22 707 220</officefax><officeemail>simulia.at.info@3ds.com</officeemail></officenameandcontact></officeentry><officeentry><officecountry>比荷卢</officecountry><officenameandcontact><officeaddress>Safariweg 14–16</officeaddress><officezip>3605 MA</officezip><officelocale>Maarssen</officelocale><altofficecountry>The Netherlands</altofficecountry><officephone> +31 346 585 710</officephone><officefax> +31 346 585 759</officefax><officeemail>simulia.benelux.support@3ds.com</officeemail></officenameandcontact></officeentry><officeentry><officecountry>加拿大</officecountry><officenameandcontact><officeaddress>3200 Greenfield Road</officeaddress><officeaddress>Suite 310</officeaddress><officelocale>Dearborn, MI</officelocale><officezip>48120</officezip><officephone> +1 313 827 5500</officephone><officeemail>simulia.greatlakes.info@3ds.com</officeemail></officenameandcontact></officeentry><officeentry><officecountry>中国</officecountry><officenameandcontact><officeaddress>Room 707–709, Tower 2</officeaddress><officeaddress>China Central Place, No. 79, Jianguo Rd.</officeaddress><address>Chaoyang District</address><officelocale>Beijing</officelocale><officezip>100025</officezip><altofficecountry>P. R. China</altofficecountry><officephone> +8610 6536 2288</officephone><officefax> +8610 6598 9050</officefax><officeemail>simulia.cn.support@3ds.com</officeemail></officenameandcontact><officenameandcontact><officeaddress>Room 806–808, Huiya Mansion</officeaddress><officeaddress>No. 1233 Lu Jia Zui Ring Rd.</officeaddress><officeaddress>Pudong District</officeaddress><officelocale>Shanghai</officelocale><officezip>200120</officezip><altofficecountry>P. R. China</altofficecountry><officephone> +8621 3856 8000</officephone><officefax> +8621 5888 9951</officefax><officeemail>simulia.cn.support@3ds.com</officeemail></officenameandcontact></officeentry><officeentry><officecountry>芬兰</officecountry><officenameandcontact><officeaddress>Falcon Business Park - Lago</officeaddress><officeaddress>Vaisalantie 2-8</officeaddress><officezip>FI-02130</officezip><officelocale>Espoo</officelocale><officephone> +358 40 902 2973</officephone><officeemail>simulia.nordic.info@3ds.com</officeemail></officenameandcontact></officeentry><officeentry><officecountry>法国</officecountry><officenameandcontact><officeaddress>10, Rue Marcel Dassault</officeaddress><officeaddress>CS70504</officeaddress><officezip>78946</officezip><officelocale>Velizy Villacoublay Cedex</officelocale><officephone> +33 1 61 62 72 72</officephone><officefax> +33 1 70 73 43 27</officefax><officeemail>simulia.fr.support@3ds.com</officeemail></officenameandcontact></officeentry><officeentry><officecountry>德国</officecountry><officenameandcontact><officeaddress>Elisabethstrae 16</officeaddress><officezip>D-52062</officezip><officelocale>Aachen</officelocale><officephone> +49 241 474 01 0</officephone><officefax> +49 241 47 40 1810</officefax><officeemail>simulia.de.info@3ds.com</officeemail></officenameandcontact><officenameandcontact><officeaddress>Sendlinger-Tor-Platz 8</officeaddress><officezip>D-80336</officezip><officelocale>Munich</officelocale><officephone> +49 89 543 48 77 0</officephone><officefax> +49 89 543 48 77 22</officefax><officeemail>simulia.de.info@3ds.com</officeemail></officenameandcontact></officeentry><officeentry><officecountry>印度</officecountry><officenameandcontact><officeaddress>ASV N RAMANAS TOWER</officeaddress><officeaddress>10th Floor, No. 37 & 38</officeaddress><officeaddress>Venkatnarayana Road, T. Nagar</officeaddress><officelocale>Chennai</officelocale><officezip>600 017</officezip><altofficecountry>Tamil Nadu</altofficecountry><officephone> +91 44 43443000</officephone><officefax> +91 44 43009770</officefax><officeemail>simulia.in.info@3ds.com</officeemail></officenameandcontact></officeentry><officeentry><officecountry>意大利</officecountry><officenameandcontact><officeaddress>Via Gioacchino Rossini 1/A</officeaddress><officezip>20020 </officezip><officelocale>Lainate MI</officelocale><officephone> +39 02 3343061</officephone><officefax> +39 02 33430645</officefax><officeemail>simulia.ity.info@3ds.com</officeemail></officenameandcontact></officeentry><officeentry><officecountry>日本</officecountry><officenameandcontact><officeaddress>Pier City Shibaura Bldg. 4F</officeaddress><officeaddress>3-18-1 Kaigan, Minato-ku</officeaddress><officelocale>Tokyo</officelocale><officezip>108-0022</officezip><officephone> +81 3 5442 6302</officephone><officefax> +81 3 5442 6259</officefax><officeemail>simulia.jp.support@3ds.com </officeemail></officenameandcontact><officenameandcontact><officeaddress>Meiji Yasuda Life Osaka Umeda Bldg. 12F</officeaddress><officeaddress>3-3-20 Umeda Kita-ku</officeaddress><officelocale>Osaka</officelocale><officezip>530-0001</officezip><officephone> +81 6 7730 2703</officephone><officefax> +81 6 7730 2708</officefax><officeemail>simulia.jp.support@3ds.com</officeemail></officenameandcontact></officeentry><officeentry><officecountry>韩国</officecountry><officenameandcontact><officeaddress>Mapo Tower 6F</officeaddress><officeaddress>418 Mapo-Dong</officeaddress><officelocale>Mapo-Gu, Seoul</officelocale><officezip>121-734</officezip><officephone> +82 2 785 6707/8</officephone><officefax> +82 2 785 6709</officefax><officeemail>simulia.kr.info@3ds.com</officeemail></officenameandcontact></officeentry><officeentry><officecountry>拉丁美洲</officecountry><officenameandcontact><officeaddress>Av. Juana Manso No. 555 7D</officeaddress><officeaddress>Dique IV</officeaddress><officezip>C1107CBK</officezip><officelocale>Puerto Madero, Buenos Aires</officelocale><officephone> +54 11 4312 8700</officephone><officefax> +54 11 4312 8700</officefax><officeemail>Horacio.Burbridge@3ds.com</officeemail></officenameandcontact></officeentry><officeentry><officecountry>北欧</officecountry><officenameandcontact><officeaddress>P.O. Box 845</officeaddress><officezip>SE-101 36</officezip><officelocale>Stockholm</officelocale><altofficecountry>Sweden</altofficecountry><officephone> +46 8 68430450</officephone><officeemail>simulia.nordic.info@3ds.com</officeemail></officenameandcontact></officeentry><officeentry><officecountry>英国</officecountry><officenameandcontact><officeaddress>Lytham House</officeaddress><officeaddress>Kelvin Close</officeaddress><officeaddress>Birchwood</officeaddress><officelocale>Warrington</officelocale><officezip>WA3 7PB</officezip><officephone> +44 1925 830900</officephone><officefax> +44 1925 885960</officefax><officeemail>simulia.uk.info@3ds.com</officeemail></officenameandcontact></officeentry></officeheading><officeheading><officeentry><officecountry>阿根廷</officecountry><officenameandcontact><officename>SMARTtech Sudamerica SRL</officename><officeaddress>Dardo Rocha 3168</officeaddress><officeaddress>Piso 2 Oficina B</officeaddress><officezip>B1640FTV-Martinez</officezip><officelocale>Buenos Aires</officelocale><officephone> +54 11 4717 2717</officephone></officenameandcontact><officenameandcontact><officename>KB Engineering</officename><officeaddress>Florida 274, Piso 3, Of. 35 </officeaddress><officezip>(1005)</officezip><officelocale>Buenos Aires</officelocale><officephone> +54 11 4326 7542 </officephone><officefax> +54 11 4326 2424</officefax></officenameandcontact><officenameandcontact><officename>Solaer Ingeniera</officename><officeaddress>Calle 21 N 295</officeaddress><officezip>(B1902DAK) La Plata</officezip><officelocale>Buenos Aires</officelocale><officephone> +54 221 489 1738</officephone></officenameandcontact></officeentry><officeentry><officecountry>巴西</officecountry><officenameandcontact><officename>SMARTtech Mecnica</officename><officeaddress>Av. Brigadeiro Faria Lima, 2894-6o.</officeaddress><officeaddress>andar Cj 63/64</officeaddress><officezip>01451-000</officezip><officelocale>Sao Paulo-SP</officelocale><officephone> +55 11 3168 3388</officephone></officenameandcontact></officeentry><officeentry><officecountry>捷克和斯洛伐克共和国</officecountry><officenameandcontact><officename>Synerma s. r. o.</officename><officeaddress>Psry 296</officeaddress><officezip>CZ-252 44</officezip><officelocale>Psry, Prague-West</officelocale><officephone> +420 603 145 769</officephone><officeemail>abaqus@synerma.cz</officeemail></officenameandcontact></officeentry><officeentry><officecountry>希腊</officecountry><officenameandcontact><officename>3 Dimensional Data Systems</officename><officeaddress>Monte Vardia, Kounoupidiana</officeaddress><officeaddress>P.O. Box 1075</officeaddress><officezip>Chania 73100</officezip><officelocale>Crete</officelocale><officephone> +30 2821040012</officephone><officefax> +30 2821040012</officefax><officeemail>support@3dds.gr</officeemail></officenameandcontact></officeentry><officeentry><officecountry>以色列</officecountry><officenameandcontact><officename>ADCOM</officename><officeaddress>Geva 17 st. 53315</officeaddress><officelocale>Givataim</officelocale><officephone> +972 3 7325311</officephone><officefax> +972 3 7325312</officefax><officeemail>shmulik.keidar@adcomsim.co.il</officeemail></officenameandcontact></officeentry><officeentry><officecountry>马来西亚</officecountry><officenameandcontact><officename>WorleyParsons Services Sdn. Bhd.</officename><officeaddress>Suite 16A, 16th Floor</officeaddress><officeaddress>Sunway Tower 2</officeaddress><officeaddress>No. 86, Jalan Ampang</officeaddress><officelocale>Kuala Lumpur</officelocale><officezip>50400</officezip><officephone> +603 2039 9000</officephone><officefax> +603 2039 9002</officefax><officeemail>abaqus.my@worleyparsons.com</officeemail></officenameandcontact></officeentry><officeentry><officecountry>墨西哥</officecountry><officenameandcontact><officename>Kimeca.NET SA de CV</officename><officeaddress>Habana 145 Tepeyac Insurgentes</officeaddress><officelocale>Mexico</officelocale><officezip>D.F.</officezip><officephone> +52 55 2459 2635</officephone><officefax> +52 55 5781 4385</officefax></officenameandcontact></officeentry><officeentry><officecountry>新西兰</officecountry><officenameandcontact><officename>Matrix Applied Computing Ltd.</officename><officeaddress>Unit 2-5, 72 Dominion Road, Mt Eden</officeaddress><officelocale>Auckland</officelocale><officezip>1024</officezip><officephone> +64 9 623 1223</officephone><officefax> +64 9 623 1134</officefax><officeemail>abaqus-tech@matrix.co.nz</officeemail></officenameandcontact></officeentry><officeentry><officecountry>波兰</officecountry><officenameandcontact><officename>BudSoft Sp. z o.o.</officename><officeaddress>Św. Marcin 58/64</officeaddress><officelocale>Poznań</officelocale><officezip>61-807</officezip><officephone> +48 61 8508 466</officephone><officefax> +48 61 8508 467</officefax><officeemail>info@budsoft.com.pl</officeemail></officenameandcontact></officeentry><officeentry><officecountry>俄罗斯、白俄罗斯和乌克兰</officecountry><officenameandcontact><officename>TESIS Ltd.</officename><officeaddress>Office 705</officeaddress><officeaddress>18, Unnatov Str.</officeaddress><officezip>127083</officezip><officelocale>Moscow</officelocale><officephone> +7 495 612 44 22</officephone><officefax> +7 495 612 42 62</officefax><officeemail>info@tesis.com.ru</officeemail></officenameandcontact></officeentry><officeentry><officecountry>新加坡</officecountry><officenameandcontact><officename>WorleyParsons Pte Ltd.</officename><officeaddress>111 Somerset Road</officeaddress><officeaddress>#12-05 TripleOne Somerset</officeaddress><officelocale>Singapore</officelocale><officezip>238164</officezip><officephone> +65 6735 8444</officephone><officefax> +65 6735 7444</officefax><officeemail>abaqus.sg@worleyparsons.com</officeemail></officenameandcontact></officeentry><officeentry><officecountry>南非</officecountry><officenameandcontact><officename>Finite Element Analysis Services (Pty) Ltd.</officename><officeaddress>Unit 3C4, The Avenues</officeaddress><officeaddress>Parklands Main Road</officeaddress><officelocale>Parklands</officelocale><officezip>7441</officezip><officephone> +27 21 556 6462</officephone><officefax> +27 21 556 7536</officefax><officeemail>feas@feas.co.za</officeemail></officenameandcontact></officeentry><officeentry><officecountry>西班牙和葡萄牙</officecountry><officenameandcontact><officename>Principia Ingenieros Consultores, S.A.</officename><officeaddress>Velzquez, 94</officeaddress><officezip>E-28006</officezip><officelocale>Madrid</officelocale><officephone> +34 91 209 1482</officephone><officefax> +34 91 575 1026</officefax><officeemail>simulia@principia.es</officeemail></officenameandcontact></officeentry><officeentry><officecountry>台湾</officecountry><officenameandcontact><officename>Simutech Solution Corporation</officename><officeaddress>10F-3, No. 129, Sungchiang Road</officeaddress><officelocale>Taipei</officelocale><officezip>10485</officezip><altofficecountry>R.O.C.</altofficecountry><officephone> +886 2 2507 9550</officephone><officefax> +886 2 2507 1811</officefax><officeemail>camilla@simutech.com.tw</officeemail></officenameandcontact></officeentry><officeentry><officecountry>泰国</officecountry><officenameandcontact><officename>WorleyParsons Pte Ltd.</officename><officeaddress>111 Somerset Road</officeaddress><officeaddress>#12-05 TripleOne Somerset</officeaddress><officelocale>Singapore</officelocale><officezip>238164</officezip><officephone> +65 6735 8444</officephone><officefax> +65 6735 7444</officefax><officeemail>abaqus.sg@worleyparsons.com</officeemail></officenameandcontact></officeentry><officeentry><officecountry>土耳其</officecountry><officenameandcontact><officename>A-Ztech Ltd.</officename><officeaddress>Bayar Cad., Gulbahar Sk., No: 15</officeaddress><officeaddress>Ege Yildiz B Blok, D.5</officeaddress><officezip>34742</officezip><officelocale>Istanbul</officelocale><officephone> +90 216 361 8850</officephone><officefax> +90 216 361 8851</officefax><officeemail>info@a-ztech.com.tr</officeemail></officenameandcontact></officeentry></officeheading></hksaddresses>

[前言](../popups/usb-pre.md)



