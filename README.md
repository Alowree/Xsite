# Production Tools

- Typora
- fix-B
- feature-C

Initially, this working directory was created to test and learn basic Git operations. While after the command of some basic Git tricks, this directory has been turned into a dropbox for some popular software tools, most of which were free for download from the Internet. 

Git安装之后，因为Windows 10的null驱动程序为停止状态，此时的Git无法正常启动，处于卡顿状态。

null.sys is a copy from A-Liang

```CMD
C:\Windows\system32>sc start null

[SC] StartService 失败 577:

Windows 无法验证此文件的数字签名。某软件或硬件最近有所更改，可能安装了签名错误或损毁的文件，或者安装的文件可能是来路不明的恶意软件。
```

禁用驱动程序强制签名

https://www.cnblogs.com/MCSFX/p/13625957.html

```CMD
C:\Windows\system32>sc query null

SERVICE_NAME: null
        TYPE               : 1  KERNEL_DRIVER
        STATE              : 1  STOPPED
        WIN32_EXIT_CODE    : 31  (0x1f)
        SERVICE_EXIT_CODE  : 0  (0x0)
        CHECKPOINT         : 0x0
        WAIT_HINT          : 0x0

C:\Windows\system32>sc start null

SERVICE_NAME: null
        TYPE               : 1  KERNEL_DRIVER
        STATE              : 4  RUNNING
                                (STOPPABLE, NOT_PAUSABLE, IGNORES_SHUTDOWN)
        WIN32_EXIT_CODE    : 0  (0x0)
        SERVICE_EXIT_CODE  : 0  (0x0)
        CHECKPOINT         : 0x0
        WAIT_HINT          : 0x0
        PID                : 0
        FLAGS              :
```

搞定！

后来重启电脑以后发现，每次null都要手动启动，很麻烦。

### Restore Default Startup Configuration for Null

1. Run the Command Prompt as an administrator.

2. Copy the commands below, paste them into the command window and press ENTER:
    ```CMD
    sc config Null start= auto
    ```
    
3. Close the command window and restart the computer.

再重启电脑以后，null就会自动开启了。
