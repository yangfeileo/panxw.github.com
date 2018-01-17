---
layout: post
category: "program"
title:  "mac直接删除文件"
tags: [代码]
---
# 在mac中填写指令 直接删除文件

1 使用Spotlight（command+space）搜索Automator
2 打开Automator 选择新建
3 选择 “服务”类型
4 在“操作”“变量”后的搜索框中输入 “运行”（英文系统输入 run） 选择运行shell脚本
5 切换“传递输入”为“作为自变量” ，并输入如下代码：

for f in "$@"
do
	if test -d "$f"
	then
		rm -r "$f"
	else
		rm "$f"
	fi
done

6 “服务”收到选定的 选“文件或文件夹”
7 保存 （command+s），存储为任意名字，比如“删除此文件”

到此删除单个文件指令完成。
可以进入finder寻找任意不需要的文件，右键，寻找到服务，找到删除此文件，即可不经过垃圾桶直接完成删除。