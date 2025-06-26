# Part4-2-Block-Design

本章節會使用你在 [`Part4-1-IP-Package`](../Part4-1-IP-Package/) 中封裝好的自訂 IP。  
請務必先完成 IP 包裝步驟，才能順利在 Block Design 中加入該 IP 進行連線與整合。

##   What is Block Design ?
Vivado 的 `Block Design` 是一個圖形化設計平台，可讓你使用拖拉方式將多個 IP 核（如 AXI IP、自訂 IP、Zynq PS 等）組合成完整系統。  
這大幅簡化了 RTL 連線與系統整合的複雜度，是進階 FPGA 開發的主流方式之一。  
>   你不會想要用寫 code 的方式去拉下面這張圖的 🙃  
>
>![Block_Design](./png/Block_Design.png)

## Part4.2.1 Create Block Design  

1.  新創一個 Vivado Project，先照著 `Part4.1.2` 的方式將 `IP_repo` import進來該 Project

2.  點選左側 `IP INTEGRATOR -> Create Block Design`，Block Design 的名稱可以自己取名  

    ![Create_Block_Design](./png/Create_Block_Design.png)  

3.  