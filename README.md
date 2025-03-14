# Build
1. Modify configure.sh to change $NDK to point to your NDK folder.
2. Uncomment corresponding flags in configure.sh to compile for different architecture. Uncomment flags for ARMv7 in addition to 32-bit ARM to compile it for ARMv7.
3. Run ```configure.sh``` to configure Samba project.
4. Run ```compile.sh``` to compile

# Install
copy out/samba dir to android 
```
mkdir -p /data/samba/private
mkdir -p /data/samba/var
mkdir -p /data/samba/etc

cp /data/samba/smb.conf /data/samba/etc/
cp /data/samba/smbpasswd /data/samba/etc/

export LD_LIBRARY_PATH=/data/samba/lib:/data/samba/lib/private
export TMPDIR=/data/local/tmp


./data/samba/bin/smbd -D
./data/samba/bin/nmbd -D


/system_ext/bin/smbd -S -F -i --no-process-group
--daemon (-D): 以守护进程方式运行 smbd，这是默认模式。
--interactive (-i): 以交互模式运行，不作为守护进程。
--foreground (-F): 在前台运行守护进程，适用于 daemontools 等工具。
--no-process-group: 不创建新的进程组。
--log-stdout (-S): 将日志输出到标准输出（stdout）。
--build-options (-b): 打印构建选项。
--port (-p): 指定监听的端口。
--profiling-level (-P): 设置性能分析级别，使用 PROFILE_LEVEL 环境变量。
这些选项通过 popt 库解析命令行参数，以便灵活配置 smbd 的行为。


```

# Reference:
   * https://github.com/google/samba-documents-provider
   * https://github.com/elliott10/samba-4.5.1
   * https://github.com/berserker/android_samba