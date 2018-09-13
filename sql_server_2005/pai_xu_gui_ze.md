### 排序规则

如 Chinese_PRC_Stroke_CS_AI_WS， 排序规则名称由两部份构成；

前半部份是指本排序规则所支持的字符集。

 Chinese_PRC 指针对大陆简体字UNICODE的排序规则。

后半部份即后缀的含义为：

 _BIN        指定使用向后兼容的二进制排序顺序。

 _BIN2      指定使用 SQL Server 2005 中引入的码位比较语义的二进制排序顺序。

 _Stroke   按笔划排序

 _CI(CS)  是否区分大小写，CI不区分，CS区分

 _AI(AS)    是否区分重音，AI不区分，AS区分

 _KI(KS)   是否区分假名类型，KI不区分，KS区分

 _WI(WS) 是否区分全半角，WI不区分，WS区分

 二进制：    二进制排序顺序既区分大小写，也区分重音。如果未选择此选项，则 SQL Server 将遵循字典中定义的相关语言或字母表的排序和比较规则。

 二进制码位：以Unicode 码位对数据进行比较或排序。对于非 Unicode 数据则使用二进制排序相同的比较方式对已排序的 SQL Server 数据进行比较的应用程序不必重新对数据进行排序。//提高性能。

 区分大小写：如果未选择此选项，则 SQL Server 认为字母的大小写形式对于排序目的而言是相同的。

 区分重音：  如果未选择此项，在排序时，SQL Server 将把字母的重音形式和非重音形式视为相同。

 区分假名：  如果未选择此选项，则 SQL Server 认为片假名字符和平假名字符对于排序目的而言是相等的。

 区分全半角：如果未选择此项，在排序时，SQL Server 将把同一字符的单字节形式和双字节形式视为相同。

附: Windows 系统的默认排序规则 ----------------------------------------------------------------------------------------------------- Windows 系统区域设置 LCID（区域设置 ID） 默认的 SQL 排序规则 Code page（代码页） 中文（台湾） 0x30404 Chinese_Taiwan_Bopomofo_CI_AS 950 中文（香港特别行政区） 0xc04 Chinese_Hong_Kong_Stroke_90_CI_AS 950 英语（香港特别行政区） 0x3c09 Latin1_General_CI_AS 1252 英语（英国） 0x809 Latin1_General_CI_AS 1252 英语（美国） 0x409 SQL_Latin1_General_CP1_CI_AS 1252 日语（Unicode） 0x10411 Japanese_Unicode 932 日语 0x411 Japanese_CI_AS 932 朝鲜语（扩展 Wansung） 0x0412 Korean_Wansung_CI_AS 949 .... .... .... .... TIP：使用 SELECT * FROM fn_helpcollations() 检索 TIP：如果未指定Windows 排序规则名称，则为创建的所有数据库分配默认排序规则 Latin1_General。 附: SQL Server 2005 版本更新以下排序规则 旧排序规则名称 新排序规则名称 ----------------------------------------------------- 日语 Japanese_90 中文 Chinese_PRC_90 Chinese_PRC_Stroke Chinese_PRC_Stroke_90 Chinese_Taiwan_Bopomofo Chinese_Taiwan_Bopomofo_90 Chinese_Taiwan_Stroke Chinese_Taiwan_Stroke_90 朝鲜语 Korean_90