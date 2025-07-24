# Part7-DMA

本章將介紹如何在 PYNQ 上使用 **Direct Memory Access (DMA)** 模組實現資料傳輸，並加速 **FFT** 運算。

## AXI Stream


## DMA Module

![DMA_Block](./png/DMA_Block.png)

DMA 在 Xilinx 提供的 IP 當中有分兩種 Mode，分別是 `Scatter Gather Mode (SG Mode)` 和 `Simple Mode`，上圖為 **Simple Mode** 下的 DMA Module。

### Port Description

| 介面名稱         | 功能描述 |
|------------------|----------|
| **S_AXI_LITE**   | 控制介面，連接至 ZYNQ PS 的 **AXI General Port (GP)**（PS端設定 DMA） |
| **S_AXIS_S2MM**  | Stream to Memory-Mapped：輸出資料寫回記憶體 |
| **M_AXIS_MM2S**  | Memory-Mapped to Stream：記憶體資料送入 FFT IP |
| **m_axi_mm2s_aclk** / **m_axi_s2mm_aclk** | DMA Clock 輸入 |
| **axi_resetn**   | Reset 訊號 |
| **introut (mm2s/s2mm)** | Interrupt 訊號，若啟用可連接至 ZYNQ7 PS 的 interrupt 控制器 |

### GP (General Purpose) port vs HP (High Performance) port

| 介面類型 | 名稱 | 資料方向 | 頻寬與用途 |
|---------|------|---------|-----------|
| **GP Port** | `AXI_GP` | PS ➜ PL / PL ➜ PS | 一般用途，低頻寬，**用於設定、控制 IP**（如 AXI Lite） |
| **HP Port** | `AXI_HP` | PL ➜ PS | **高頻寬**，適合 DMA 讀取寫入 DDR 使用 |

## FFT Module

## Part 7.1 Vivado Block Design

1. Create a new Vivado Project and Create a new Block Design
2. 