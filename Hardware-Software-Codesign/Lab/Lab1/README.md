# FPGA Design Lab1

使用 PYNQ-Z2 上的 Zynq Processor 操作一個簡單的 C/C++ 排序 Project。

## Problem 1
使用鍵盤輸入五個非負整數後，透過 PS 端去將此數列由小到大排序。

> 💡 **Hint：** Block design 可以參考 Part1 的設計即可。



參考輸出結果 :
![](png/answer.png)


## Problem 2 
在這個lab中，學習如何使用 UART 在 PC 和 PYNQ 之間進行通訊。PC 會透過 UART 傳送一張圖片到 PYNQ，PYNQ 會將原始圖片經過二值化處理後，最後再將轉換後的圖片傳回給 PC。
