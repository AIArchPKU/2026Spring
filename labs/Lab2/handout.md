---
layout: page
title: Lab2 5-Stage Pipelined MIPS CPU
---

# 五级流水线处理器 (100pts)

在此 Lab 中，你将完成一个简化的 5-Stage MIPS CPU，通过补全 Verilog 代码，使得每条指令能被正确执行。

## 1. 背景简介

本实验采用 MIPS 的 5 阶段流水线结构：

1. **IF** - Instruction Fetch
2. **ID** - Instruction Decode
3. **EX** - Execute
4. **MEM** - Memory Access
5. **WB** - Write Back

为了降低实现难度，本 CPU 不实现真正的流水线并发执行。**每次仅执行一条指令，完成所有阶段后再启动下一条**，无需处理数据冒险、控制冒险和 Forwarding。（也就是说只有一条指令 WB 完成之后，IF 才会 Fetch 下一条指令）


## 2. 项目结构说明

在课程共享文件的 `/mnt/nfs` 文档下，你能看到 `Lab2` 文件夹，其中包含了此任务需要的代码。你需要将此文件夹复制到自己的主目录以进行编辑；

你将在如下文件结构下完成实验：

```
├── Makefile
├── run_tests.sh              # 自动运行测试用例脚本
├── setup_env.sh              # 配置环境脚本
├── testbench/                # 测试平台及可视化
│   ├── testbench.v           # 主测试平台
│   └── ...
├── test_progs/               # 测试指令程序（汇编 .s 文件）
│   └── *.s                   # 示例程序文件
├── verilog/                  # 你将完成的核心 Verilog 文件
│   ├── pipeline.v            # 顶层模块
│   ├── if_stage.v            # IF 阶段实现
│   ├── id_stage.v            # ID 阶段实现
│   ├── ex_stage.v            # EX 阶段实现
│   ├── mem_stage.v           # MEM 阶段实现
│   ├── wb_stage.v            # WB 阶段实现
│   ├── regfile.v             # 通用寄存器文件
│   ├── icache.v              # 指令缓存（可作为黑盒使用）
│   └── cachemem.v            # 数据缓存（可作为黑盒使用）
└── vs-asm                    # 汇编工具，用于生成测试程序二进制
```


## 3. 你的任务

所有需要填空的地方都会用以下代码块标注：

```verilog
// 在此处插入你的代码
// 这里有任务详情的注释
// Insert your code below

... Your code here ...

// Insert your code above
```

你需要在 verilog/ 目录下的以下文件完成 Lab（详情可以参考文件中的注释）：

1. if_stage.v: ~5行代码
    
2. id_stage.v: ~15行代码
    
3. ex_stage.v: ~15行代码
    
4. mem_stage.v: <5行代码
    
5. wb_stage.v: ~5行代码
    
6. pipeline.v: ~10行代码
    


## 4. 运行与测试

### 环境配置

运行前你需要执行 Lab 文件夹中的 `setup_env.sh` 以配置环境，此操作需要使用 sudo：

```verilog
sudo ./setup_env.sh
```

### 编译 Verilog 代码

你可以使用 `make all` 来编译CPU；可以使用 `make nuke` 清除编译产生的文件；

此后，你可以使用 `run_tests.sh -t <path to test program>` 来运行特定的测试任务，也可以不带参数运行此脚本以进行完整的测试。

```bash
$ ./run_tests.sh -h
USAGE: ./run_tests.sh [OPTIONS]

This script runs one or all the tests against both this processor's output and golden processor's output

OPTIONS:
  -h, --help             Show this message
  -t, --test FILE        Specific test program to run (can be specified multiple times for more tests)
  -q, --quiet            Run in non-interactive mode
```

### 关于 Debug

在你完成 CPU 实现后，运行测试程序将自动生成多个调试输出文件。每个文件提供不同层次的信息，帮助你理解 CPU 在每个周期做了什么，哪里可能出错了。

Tips：假如你运行测试程序很久还没有输出，那很有可能是CPU死循环了，需要排查是否错误地发生了stall；

### 输出文件说明

| **文件名格式** | **内容简介** |
| --- | --- |
| \<test_program.s\>_detailed.csv | **每个周期各阶段的详细信号变化**（包括寄存器值、ALU输出、控制信号、PC等），适合深入单步追踪执行流程。 |
| \<test_program.s\>_memory.out | 程序运行结束后，**内存中数据的最终状态**。 |
| \<test_program.s\>_pipeline.out | **流水线五个阶段在每个周期的执行情况**（即哪条指令在哪个阶段），尽管本 Lab 中是顺序执行，也可用于观察执行是否正确。 |
| \<test_program.s\>_program.out | 仿真器的输出：辅助验证整体行为。 |
| \<test_program.s\>_writeback.out | 每次进入 WB 阶段时，**写回的寄存器编号、值和对应的 PC。** |


你可以在 ./golden_result 里面找到期望的输出，并用于参考；


## 5. 截止日期与提交要求

> **截止日期：2026.06.13 23:59** 


1. 压缩为zip格式的实现的 Verilog 文件（提交整个 verilog/ 目录）
    
    你可以通过 `make submit` 来快速生成一个zip文件；
    
2. 简略的实验报告，包含：
    - 实现思路
    - 你调试时遇到的关键问题及解决方案
    - **注意：报告不超过 2 页**