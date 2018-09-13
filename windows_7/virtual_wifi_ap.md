### Virtual Wifi AP {#virtual-wifi-ap}

@echo off

:begin

cls

echo Windows 虚拟wifi共享,请用管理员身份运行

echo ****************************************

echo 功能选择: 1-用原有的SSID和key启动

echo           2-设置新的SSID和key并启动

echo           3-显示虚拟wifi状态

echo           4-关闭虚拟wifi网卡

echo ****************************************

choice /C 1234 /M &quot;请输入数字： &quot;

if errorlevel 4 goto stop

if errorlevel 3 goto show

if errorlevel 2 goto new

if errorlevel 1 goto start

if errorlevel 0 goto end

:start

netsh wlan start hostednetwork

goto end

:new

set/p x=请输入SSID：

set/p y=请输入key:  

netsh wlan set hostednetwork mode=allow ssid=%x% key=%y%

echo 请打开控制面板，设置需要共享的网络，完成后按任意键继续...

@pause

netsh wlan start hostednetwork

goto end

:show

netsh wlan show hostednetwork

goto end

:stop

netsh wlan set hostednetwork mode=disallow

:end

echo ****************************************

choice /T 10 /C YN /D N /M &quot;是否继续操作(10秒后默认选择N):&quot;

if errorlevel 2 goto close

if errorlevel 1 goto begin

:close

pause