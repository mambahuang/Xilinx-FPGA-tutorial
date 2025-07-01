# FPGA Design Lab2

利用 AXI-GPIO 搭配 Vitis 設計一個簡易紅綠燈。


以 RGB led4 做為紅綠燈，並且在 terminal 上顯示目前的燈號以及剩餘秒數。  

---
每個燈號的維持時間由 sw0 來控制。  

| sw0 | Green | Yellow | Red |
|-------|-------|-------|-------|
| 0 | 15 秒 | 1 秒 | 16 秒 |
| 1 |  7 秒 | 1 秒 |  8 秒 |


