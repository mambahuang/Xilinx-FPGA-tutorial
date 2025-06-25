# Part1. Vivado Basic Tutorial

## Part 1.1 Board File
1.  根據你所使用的 FPGA Board 去其官方網站下載對應的 Board File，這樣 Vivado 才能辨識並正確套用該板子的配置。

2.  以下以 PYNQ-Z2 為例，說明如何安裝 Board File：

3.  **前往該塊板子的官網下載 Board File**  
    https://www.e-elements.com.tw/en/products-en/xup-pynq/pynq-z2/  
    ![Website](./png/PYNQ_Z2_Website.png)  
    - `Board File`：包含板子資訊，用於 Vivado 自動載入設定。
    - `Master XDC`：包含 I/O 腳位限制，需匯入 Vivado 專案中以對應硬體連接腳位。  
    > **備註：建議現在就先下載 Master XDC**
    > 
    > `Master XDC` 檔案會在後續建立 RTL 設計並做實體實作（Implementation）時使用，  
    > 它用來定義 FPGA 腳位與外部元件（如按鈕、LED、時脈）的對應關係。  
    > 為了後續方便，建議此階段就一併下載並妥善保存。


4.  **安裝 Board File：**
    - 請將解壓後的 `pynq-z2` 資料夾放入以下路徑中：

      ```
      <你自訂的 Vivado 安裝目錄>\<version>\data\boards\board_files\
      ```  
      ![Board_File_Path](./png/Board_File_Path.png)  
      
    - 若 `board_files` 或上層資料夾不存在，請自行手動創建。

5. **完成後重啟 Vivado**，在 Create Project → Board 頁面中即可選擇 `PYNQ-Z2` 板子。

## Part 1.2 Create Vivado Project

1.  點開 Vivado 並且按下 Create Project  

    ![Create](./png/create_project.png)  

2.  自行選擇路徑，切記路徑不得出現**中文**  

    ![Path](./png/path.png)

3.  選擇 RTL project ，若有寫好的 RTL code 則不必勾選 `Do not specify sources at this time`，可以在此階段將 RTL code 跟 Design Constraint import 進 project 中  

    ![Project_type](./png/Project_type.png)  

4.  選擇 FPGA Board ，這邊以 Pynq-Z2 做舉例  

    ![Board_select](./png/board_select.png)  

5.  若成功創建 Project 後 Vivado 將呈現下方的畫面  

    ![Project_done](./png/project_done.png)  

## Part 1.3 Introduction to Vivado Gui  

![Vivado_GUI](./png/Vivado_GUI.png)  

1.  **Project Manager**  

    整個 Project 的管理包括了 : 檔案管理 , 專案設定 , IP資料夾路徑等等，後續到了其他的設計階段(e.g. synthesis / implementation )要回到修改程式或新增檔案的部分都需按 `Project Manager` 回去才可以做修改。  

2.  **IP Integrator**

    以 `Block Design` 的方式來兜出整個系統，且可以加入 Xilinx 或是第三方所提供的 IP 來實作整個系統的設計

3.  **Synthesis** 

    將設計好的硬體描述檔合成成 FPGA 上由 CLB , Switch Box , Embedded Element 等元件所組成的實際電路

4.  **Implementation**  

    將合成好的實際電路擺放到 FPGA 上的確切位置 (Floor & Plan)

5.  **Program And Debug**  

    Generate Bitstream : 將 Implementation 完的電路編譯成一個燒錄進 FPGA 的位元串流檔

6.  **Sources**  

    管理 `Design Sources` , `Constraints` , `Simulation Sources`

7.  **Tcl Console**  

    使用指令的方式來實作 Project (在 GUI 上每個點選的動作其實都有相對應的一條指令，也會顯示在這邊)  

    - Message : 任何系統訊息, warning, error 都會顯示在這，若在實作 project 時卡關建議先到這裡找問題  

    - Log : 紀錄 Project 歷程  

    - Reports : 回報 synthesis & implementation 如 timimg, power, utilization 等資訊  

    - Design Runs : 顯示軟體現在正在進行什麼步驟  

8. **專案設定總覽**  
   完成 Create Project 後， Vivado 會顯示如圖所示的專案基本設定，包括：
   - Project name
   - Project location
   - Product family / Project part
   - Top module name

9.  **當前使用之FPGA資訊**  

10. **Synthesis & Implementation 之 Summary**
    顯示 Synthesis 與實作 Implementation 的狀態，包括：
    - Status
    - Warning 訊息數量
    - 使用之晶片型號（Part: xc7z020clg400-1）