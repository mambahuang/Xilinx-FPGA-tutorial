# FPGA Design Lab3

在本次 Lab 中，將結合 Xilinx 提供的 IP 與自行設計的 IP，建立一個完成加法運算的系統。

系統流程為：
   - (1) 使用 CDMA 將資料傳送至 Block Memory。
   - (2) 硬體 IP 從 Bram 中讀取資料後進行乘法運算。
   - (3) 硬體 IP 將計算完成的結果儲存回 Bram 內。
   - (4) 運算完成後，CDMA 將結果搬回 ZYNQ。


本次 Lab 有提供完成的 add.v 檔案，請自行將其包裝成可在 Vivado 中使用的 IP，並完成整體系統的建構與對應的 Jupyter 軟體設計。

## 系統架構圖

![](png/system.jpg)

注意 AXI smartConnect 間 master 和 slave 的關係。
在 ZYNQ Processing System 上需要多加入一個 slave port 給 CDMA 使用。

點選   
` ZYNQ7 Processing System IP > PS-PL Configuration > HP Slave AXI Interface >  S AXI HP0 interfate `✅

![](png/PS_HP0.png)


---  

Block design 的 address Editor可自行設定。  
> 📌 特別注意/processing_system7_0/S_AXI_HP0 的 slave segment。  
配置任何 master 的 address 必須完全落在 0x00000000 到 0x1FFFFFFF 這個範圍內。
 同時也要對齊（比如 1MB 對齊，32-bit 對齊等）。

![](png/address.png)

---

add IP 的 clk 和其他 ip 的 aclk 等腳位接同一 clk 訊號即可，rst 為負緣觸發，接在Process System Reset的peripheral_aresetn上即可。

![](png/add_ip.png)

其餘 Bram 設定請自行判斷。

## 參考 Block diagram

![](png/block_diagram.png)


---
## 測試結果範例

![](png/demo.png)