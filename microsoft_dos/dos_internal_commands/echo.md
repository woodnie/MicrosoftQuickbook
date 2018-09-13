#### echo {#echo}

echo

表示显示此命令后的字符

echo off

表示在此语句后所有运行的命令都不显示命令行本身

@

与echo off相象，但它是加在其它命令行的最前面，表示运行时不显示命令行本身。

call

调用另一条批处理文件（如果直接调用别的批处理文件 ，执行完那条文件后将无法执行当前文件后续命令）

pause

运行此句会暂停，显示Press any key to continue... 等待用户按任意键后继续

rem

表示此命令后的字符为解释行，不执行，只是给自己今后查找用的

　　例：用edit编辑a.bat文件，输入下列内容后存盘为c:\a.bat，执行该批处理文件后可实现：将根目录中所有文件写入 a.txt中，启动UCDOS，进入WPS等功能。电+脑*维+修-知.识_网(w_ww*dnw_xzs*co_m)

　　批处理文件的内容为: 　　　　　　　　文件表示：

　　　　echo off　　　　　　　　　　　　不显示命令行

　　　　dir c:\*.* &gt;a.txt　　　　　　　将c盘文件列表写入a.txt

　　　　call c:\ucdos\ucdos.bat　　　　调用ucdos

　　　　echo 你好 　　　　　　　　　　　显示&quot;你好&quot;

　　　　pause 　　　　　　　　　　　　　暂停,等待按键继续

　　　　rem 使用wps 　　　　　　　　　　注释将使用wps

　　　　cd ucdos　　　　　　　　　　　　进入ucdos目录

　　　　wps 　　　　　　　　　　　　　　使用wps　　

　　批处理文件中还可以像C语言一样使用参数，这只需用到一个参数表示符%。电+脑*维+修-知.识_网(w_ww*dnw_xzs*co_m)

　　 %表示参数，参数是指在运行批处理文件时在文件名后加的字符串。变量可以从 %0到%9，%0表示文件名本身，字符串用%1到%9顺序表示。电+脑*维+修-知.识_网(w_ww*dnw_xzs*co_m)

　　例如，C：根目录下一批处理文件名为f.bat，内容为 format %1

　　则如果执行C:\&gt;f a: 　　　则实际执行的是format a:

　　又如C：根目录下一批处理文件的名为t.bat，内容为 type %1 type %2

　　那么运行C:\&gt;t a.txt b.txt 将顺序地显示a.txt和b.txt文件的内容