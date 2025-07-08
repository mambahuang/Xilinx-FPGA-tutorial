# FPGA Design Lab5

本次 lab 請使用 DSP 模組來實做 Convolution sysem。

  >   📌為什麼 DSP 適合做 Convolution？
  > 
  > 因為 convolution 的本質是大量的乘法與加法（MAC）運算，而 DSP 模組剛好內建乘加結構，能在一個時鐘週期內完成這種運算。相較用邏輯電路實作，DSP 不但運算更快、資源更省，還能支援固定點計算與並行處理，非常適合用來加速影像處理、濾波器等 convolution 應用。

## Step 1 
先使用 `.tcl` 去還原出 convolution system 的 project。

詳細 project 介紹請看 [Lab7-Convolution-system](./Lab7-Convolution-system/) 。


## Step 2 
將 IP 中的 MAC 運算使用 `DSP48E1` 來完成。

![](png/MAC.png)

### 怎麼用 DSP48E 的 Cascade 方式完成「大位數乘法」?

> 📌 Xilinx DSP48E 基本規格回顧
>
> | Port    | 寬度限制   | 支援 signed? |
> |---------|------------|:------------:|
> | A       | 25 bits    | ✅ Yes       |
> | B       | 18 bits    | ✅ Yes       |
> | C       | 48 bits    | ✅ Yes       |
> | P (輸出)| 48 bits    | ✅ Yes       |


### 方法一：手動拆解 + 多顆 DSP 相乘再加總

將兩個 32-bit signed 數拆成 高 16-bit 和 低 16-bit。

![](png/AB.png)

依序使用 4 個 DSP48 實作乘法。

---

### 方法二：使用 Vivado HLS（High-Level Synthesis）
可以用 `C/C++` 撰寫程式，然後讓 `HLS` 自動產生 RTL（Verilog/VHDL）和對應的 `DSP48E1` 實現。

### ✅ 一、準備工具

安裝並開啟使用 `Vitis HLS`（Vivado 2021.1 之後）

### ✅ 二、基本流程
1. 打開 Vitis HLS
![](png/HLS_2023.png)
2. 新建一個 project

3. 撰寫 `C/C++ code`（如 32×32 乘法）
![](png/HLS_source.png)

4. 寫 `Testbench`（用來驗證功能）

5. 執行 `C simulation` 測試
![](png/HLS_simulation.png)

6. 設定 `Top function` : 左上方 `Project` > `Project settins` > `Synthesis` 選擇 top function。
![](png/HLS_top.png)


6. 按下 `C Synthesis` 產生 `RTL`
![](png/HLS_synthesis.png)

7. 查看報告確認 `DSP` 有被使用
![](png/HLS_report.png)

8. 匯出 `RTL` 到 `Vivado block design`
![](png/HLS_RTL.png)
