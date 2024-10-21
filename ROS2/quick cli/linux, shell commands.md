# Export
- export 可新增，修改或删除环境变量，供后续执行的程序使用
- export 的效力仅限于该次登陆操作
- 语法：
```shell
export [-fnp][变量名称]=[变量设置值]
```
例 
```shell
export PATH=$PATH:/home/ay2021/scripts
```
![[Pasted image 20240313151213.png|700]]

# Source
- 作用：执行 filename 这个文件中的命令

# 怎么关掉某个进程
- Sudo top 查看进程，并记住要杀掉的进程的 PID
- Sudo kill `PID_number`
- 