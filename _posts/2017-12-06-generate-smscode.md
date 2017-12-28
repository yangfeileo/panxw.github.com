---
layout: post
category: "read"
title:  "记一次代码学习记录"
tags: [阅读,人生]
---

# 记一次代码学习记录

        场景：生成6位验证码


        public int ComputeTotp(/*HashAlgorithm hashAlgorithm, ulong timestepNumber, string modifier = null*/)
        {
            var hashAlgorithm = new HMACSHA1();
            var timestepNumber = (ulong)DateTime.UtcNow.Ticks;

            byte[] bytes = BitConverter.GetBytes(IPAddress.HostToNetworkOrder((long)timestepNumber));
            var steam = new MemoryStream(bytes);
            byte[] array = hashAlgorithm.ComputeHash(/*Rfc6238AuthenticationService.ApplyModifier(bytes, modifier)*/steam);
            int num = (int)(array[array.Length - 1] & 15);
            int num2 = (int)(array[num] & 127) << 24 | (int)(array[num + 1] & 255) << 16 | (int)(array[num + 2] & 255) << 8 | (int)(array[num + 3] & 255);
            return num2 % 1000000;
        }