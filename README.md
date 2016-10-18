# TUOJ Problem Lab

这是 TUOJ 开发的子项目 ProblemLab。

## 进度

+ format (ing.)
+ interaction (ing.)
+ omniauth
+ limitation

## 题目格式

格式样例见 ProbSample 。目录的必要结构如下：

	- problem
		- doc \\ 问题描述、题解等，非评测环境相关
		- files \\ 未编译评测环境
		- data \\ 测试数据
		- etc \\ 配置文件
			- conf \\ 题目信息
			- init \\ 部署引导
		[- test] \\ 提交测试，标程等
		[- down] \\ 下发文件
		[- your other files: README.md, etc.]

## 部署

`etc/init` 用于题目的部署。包括 make 评测环境、数据等。`init` 支持以下命令：

	compile <file> \\ 按 file 的后缀名编译
	make		   \\ 调用 files/make
	gendata 	   \\ 按 conf 申明，事先调用 generator 生成数据

你可以设置每个命令所需要的权限。一般来说 make 和 gendata 都是应严格限制的命令。 

##
