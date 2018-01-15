---
layout: post
category: "program"
title:  "邮件检查程序"
tags: [代码]
---

# mailcheck program


    //姓名列表存在namelist.txt文档中，供以后处理方便
    var text = File.ReadAllText("namelist.txt");
    
    //执行读取操作
    using (var reader = new StringReader(text))
    {
        ReadNames(reader);
    }   
    
    //此处使用异步获取方式 防止程序的卡顿
    public async void ReadNames(StringReader reader)
    {
        string str;
        while ((str = await reader.ReadLineAsync()) != null)
        {
            if (String.IsNullOrWhiteSpace(str))
                continue;
            nameList.Add(str.Trim());
        }
    }