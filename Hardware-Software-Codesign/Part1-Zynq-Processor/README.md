# Part1-Zynq-Processor

Zynq 不僅是一顆 FPGA，它還內建了完整的處理系統，包括：

-   雙核心 ARM Cortex-A9 處理器

-   DDR 記憶體控制器、各類 I/O 介面（UART、SPI、USB…）

-   AXI 匯流排（用來與 PL 做資料交換）

-   可選擇執行 Linux、PetaLinux、Ubuntu 或 Baremetal 程式

這些處理功能（包含 ARM 處理器、DDR 控制器、AXI 匯流排等）在晶片內部是以 Hard IP 的形式存在。

-   PS（Processing System）是預先實作在 Zynq 晶片上的電路區塊，不像 PL 是可程式化邏輯。

-   使用者無法改變其結構（例如 CPU 架構、I/O 分配等），但可以透過 Vivado 的介面啟用、設定、連接。

-   開發者可以透過 **Vivado Block Design** 中的 **ZYNQ7 Processing System IP** 對 PS 做配置，例如選擇是否開啟 USB、Ethernet、UART、SD 卡等功能。


## Part1.1 Running a Basic UART Application on Zynq PS

在本次實作中，我們將示範如何**僅使用 Zynq PS（Processing System）** 的資源 **（不連接 PL 邏輯）**，利用 ARM Cortex-A9 處理器進行簡單的資料處理並透過 UART 傳回結果。

1.  Create a New Vivado Project

2.  Create Block Design

3.  點選 Block Design 內的 `+`，搜尋 `ZYNQ7 Processing System`，並加入 Block Design 當中  

    ![Add_Zynq](./png/Add_Zynq.png)
    ![Add_Zynq_Done](./png/Add_Zynq_done.png)

4.  點選上方綠色橫幅 `Run Block Automation`， Vivado會自動幫你完成一些連接線的設置

    ![Run_Block_Automation](./png/Run_Block_Automation.png)

    連接完成後會跳出 `DDR` 、 `FIXED_IO`  

    ![Automation_Done](./png/Automation_Done.png)

    -   **DDR** : Zynq PS 與外部 DDR3 記憶體的連接 Port
    -   **FIXED_IO**    : Zynq PS 對外部週邊 I/O 的接口

5.  對 ZYNQ7 點兩下進行 `customize`，本次實驗只需用到 ZYNQ processor 本身，所以要把沒用到的 I/O 取消。 

    ![Customization_Panel](./png/Customization_Panel.png)
