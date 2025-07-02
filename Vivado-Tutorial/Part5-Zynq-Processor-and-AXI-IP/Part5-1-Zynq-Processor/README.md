# Part5-1 Zynq Processor

## What is Zynq ?
Zynq SoC 是結合了 PS(Processor System) 和 PL(programmable Logic) 的裝置
- PS (Processor System) : 硬體內建 ARM Cortex-A9 雙核心處理器 (Zynq-7000系列) 加上 caches、on-chip memory、還有其他peripherals (UART, I2C, etc.) 。
- PL (Programmable Logic) : 可自定義邏輯的 FPGA 區塊，也就是使用者可以自己設計特定功能的 IP ，像是加解密模組、影像處理器、DMA模組等。

![zynq_intro](./png/zynq_intro.png)

## What is PYNQ ?
PYNQ = Python + ZYNQ，就是將 Xilinx ZYNQ 的部分功能 Python 化，直接使用 Python 資料庫與 FPGA硬體進行功能的開發。
![pynq1](./png/pynq1.png)
![pynq2](./png/pynq2.png)
