# Part4-BRAM

## What is BRAM?
BRAM（Block RAM）是 FPGA 內建的一種高速記憶體資源，專門用於儲存大量資料，可由`邏輯電路`或 `ZYNQ 的 ARM 核心` 進行讀寫。與外部記憶體（ DDR ）相比，BRAM 擁有更快的存取速度與更低的延遲，適合用於對速度與時序要求較高的應用。

## BRAM in Zynq-7020
Zynq-7000 系列中的 Zynq-7020 SoC，內部 PL 中提供：  

| 資源類型 | 數量 | 說明 |
| ------- | -----| --- |
| **36K BRAM blocks** | 140 個 | 每個 Block 為 36Kbits（4.5KB），可配置為 Single Port 或 Dual Port 記憶體 |
| **總容量** | 約 630KB | 合計容量為 140 × 4.5KB ≈ 630KB |


## Part 4.1 BRAM Configuration

1.  Create a New Vivado Project and Create a New Block Design

2.  加入 `Block Memory Generator`

    ![BRAM_Add](./png/BRAM_Add.png)

3.  進入該 IP 設定頁面  

    ![BRAM_Config](./png/BRAM_Config.png)  

### Mode:
| Mode | 說明 |
| ------- | ---- |
| **BRAM Controller** | 搭配 Vivado 中的 AXI BRAM Controller IP 使用，由 AXI 控制 BRAM Controller 來生成 BRAM 讀取寫入所需的訊號。可透過軟體端對該BRAM進行寫入讀取。 |
| **Standalone** | 不搭配 `BRAM Controller`來使用，無法由軟體直接存取，需由硬體自行管理資料的讀寫時序與內容，但在細節配置上更靈活。|

## Part 4.2 Standalone BRAM
在進行純硬體設計（Pure RTL or Block Design without Processor）的情境下，BRAM（Block RAM）是我們在 FPGA 裡最常用來儲存大量資料的元件。




## Part 4.3 BRAM Controller

