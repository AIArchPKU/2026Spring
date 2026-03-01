---
layout: page
title: Project
permalink: /project/
---

# Preparing

本课程Lab将依托于[CLab](https://clab.pku.edu.cn)进行。你需要在CLab上创建用于本课程的主机，具体步骤见[CLab使用指南](/static_files/Lab/Preparing/clab_usage.html)。

> ❗️**本课程主机会在课程结束后随时被回收，请及时备份你的数据。**

要进行本课程的实验，你可能需要一些基本的Linux操作系统知识。如果你对Linux操作系统不熟悉，可以参阅 MIT 的 [missing semeter](https://missing.csail.mit.edu/2020/) （中文翻译版：[计算机教育中缺失的一课](https://missing-semester-cn.github.io/)）。

# Lab 1
在本次实验中，你将：
 - 用Verilog编写一个基本的1D Winograd计算模块；
 - 编写一个cordic计算单元，用于计算cos和sin函数;
 - Bonus (optional): 利用cordic计算单元实现一个基本的FFT模块；
 - Bonus (optional): 实现一个2D Winograd卷积模块。

实验具体要求可见[Lab 1](/static_files/Lab/Lab1/lab1_handout.html)。

参考资料:
 - [CORDIC - Wikipedia](https://en.wikipedia.org/wiki/CORDIC)
 - [Fast Algorithms for Convolutional Neural Networks](https://arxiv.org/abs/1509.09308)
 - [Cooley–Tukey FFT algorithm - Wikipedia](https://en.wikipedia.org/wiki/Cooley%E2%80%93Tukey_FFT_algorithm)

**Due: 2025-04-10 23:59:59**

请在截止日期前，将代码及不超过3页的实验报告提交到教学网。（如果你完成了Bonus部分，你需要附上你编写的Testbench及波形截图）


# Lab 2
在本次实验中，你将完成一个 5 Stage 的 MIPS 流水线 CPU；

实验具体要求可见[Lab 2 Handout](static_files/Lab/Lab2/lab2_handout.html)。

参考资料:
 - [MIPS Instruction Formats](static_files/Lab/Lab2/Instruction_Formats.pdf)
 - [MIPS Instruction Descriptions](static_files/Lab/Lab2/Instruction_Descriptions_Short.pdf) ([Detailed version](static_files/Lab/Lab2/Instruction_Descriptions_Long.pdf))

**Due: 2025-06-15 23:59:59**

请在截止日期前，将代码及不超过2页的实验报告(具体要求见Lab 2 Handout文件)提交到教学网。

# Lab 2 bonus
在本实验中，你将完成一个AI卷积加速器的设计；

实验具体要求见[Lab 2 bonus Handout](static_files/Lab/Lab2/Lab2_bonus.pdf)

**Due: 2025-06-15 23:59:59**