---
title: 步驟 1：建立專案並將資料表新增至表單 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c49a3e9ac7c4a37c1c030d631667d90b274143cf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934687"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>步驟 1：建立專案並將資料表加入至表單
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

建立配對遊戲的第一個步驟就是建立專案並將資料表加入至您的表單。 資料表可協助依 4x4 格線對齊圖示。 您也可以設定多個屬性來強化遊戲面板的外觀。  
  
### <a name="to-create-a-project-and-add-a-table-to-your-form"></a>若要建立專案並將資料表加入至表單  
  
1. 在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。  
  
2. 如果您不是使用 Visual Studio Express，則必須先選取程式設計語言。 從 [安裝的範本] 清單中選擇 [Visual C#] 或 [Visual Basic]。  
  
3. 在專案範本清單中，選擇 [Windows Forms 應用程式]，並將專案命名為 **MatchingGame**，然後選擇 [確定] 按鈕。  
  
4. 在 [屬性] 視窗中，設定下列表單屬性。  
  
   1.  將表單的 **Text** 屬性從 [Form1] 變更為 [Matching Game]。 此文字會出現在遊戲視窗的頂端。  
  
   2.  將表單的大小設定為寬度 550 像素乘以高度 550 像素。 您可以將 **Size** 屬性設定為 [550, 550]，或是拖曳表單的角落直到您在整合式開發環境 (IDE) 的右下角看見正確的大小為止，以執行此動作。  
  
5. 選擇 IDE 左側的 [工具箱] 索引標籤，以顯示工具箱。  
  
6. 從工具箱中的 [容器] 類別拖曳 `TableLayoutPanel` 控制項，然後為其設定下列屬性。  
  
   1. 將 **BackColor** 屬性設定為 [CornflowerBlue]。 若要這麼做，請在 [屬性] 視窗中選擇 **BackColor** 屬性旁的下拉式箭頭，開啟 [BackColor] 對話方塊。  然後，請在 [BackColor] 對話方塊的 [Web] 索引標籤，以檢視可用的色彩名稱清單。  
  
      > [!NOTE]
      >  色彩不是以字母順序排序，CornflowerBlue 位在靠近清單底部的位置。  
  
   2. 選擇屬性旁邊的下拉式按鈕，然後選擇大型中間按鈕，將 **Dock** 屬性設定為 [Fill]。 如此可將資料表延伸，使其涵蓋整個表單。  
  
   3. 將 **CellBorderStyle** 屬性設定為 [Inset]。 如此可在面板的每個儲存格之間提供可見的框線。  
  
   4. 選擇 TableLayoutPanel 右上角的三角形按鈕，以顯示其工作功能表。  
  
   5. 在工作功能表上，選擇 [新增資料列] 兩次，以便再新增兩個資料列，然後選擇 [新增資料行] 兩次，以便再新增兩個資料行。  
  
   6. 在工作功能表上，選擇 [編輯資料列與資料行] 以開啟 [資料行和資料列樣式] 視窗。 選擇每一個資料行，並選擇 [百分比] 選項按鈕，然後將每一個資料行的寬度設定為總寬度的 25%。 然後從視窗頂端的下拉式方塊中選取 [資料列]，並將每一個資料列的高度設為 25%。 當您完成時，請選擇 [確定] 按鈕。  
  
      您的 TableLayoutPanel 現在應該有 4x4 的格線，其中內含 16 個大小相等的方形儲存格。 這些資料列和資料行是稍後會顯示圖示影像的地方。  
  
7. 確定已在表單編輯器中選取 TableLayoutPanel。 若要驗證這一點，您應該會看到 [tableLayoutPanel1] 位於 [屬性] 視窗的上方。 如果未選取該項目，請選取表單上的 TableLayoutPanel，或是在 [屬性] 視窗上方的下拉式控制項中選取它。  
  
    選取 TableLayoutPanel 時，請開啟工具箱，然後將 [Label] 控制項 (位於 [通用控制項] 類別) 新增至 TableLayoutPanel 的左上角儲存格。 `Label` 控制項現在應該已在 IDE 中選取。 為其設定下列屬性。  
  
   1.  請確定將標籤的 **BackColor** 屬性設定為 [CornflowerBlue]。  
  
   2.  將 [AutoSize] 屬性設定為 [False]。  
  
   3.  將 **Dock** 屬性設定為 [Fill]。  
  
   4.  選擇屬性旁的下拉式按鈕，然後選擇中間按鈕，以將 **TextAlign** 屬性設定為 [MiddleCenter]。 這可確保圖示會顯示在儲存格的中央。  
  
   5.  選擇 **Font** 屬性。 應該會出現省略符號 (…) 按鈕。  
  
   6.  選擇省略符號按鈕，並將 [字型] 值設定為 [Webdings]、將 [字型樣式] 設定為 [粗體]，並將 [大小] 設定為 [72]。  
  
   7.  將標籤的 **Text** 屬性設定為字母 **c**。  
  
        TableLayoutPanel 中的左上角儲存格現在應該包含一個黑色方塊 (位於藍色背景中央)。  
  
       > [!NOTE]
       >  Webdings 字型是 Windows 作業系統隨附的圖示字型。 在配對遊戲中，玩家必須將圖示配對，因此您會使用此字型來顯示要配對的圖示。 不要將 **c** 放在 **Text** 屬性中，請嘗試輸入不同字母，看看顯示的圖示為何。 驚嘆號是一隻蜘蛛、大寫 N 是眼睛，而逗號則是一個辣椒。  
  
8. 選擇您的 Label 控制項並將其複製至 TableLayoutPanel 中的下一個儲存格 (選擇 Ctrl+C 鍵，或是依序選擇功能表列上的 [編輯] 和 [複製])。然後將它貼上  (選擇 Ctrl+V 鍵，或是依序選擇功能表列上的 [編輯]和 [貼上])。第一個標籤的複本會顯示在 TableLayoutPanel 的第二個儲存格中。 再次將它貼上，而另一個標籤會顯示在第三個欄框中。 持續貼上 `Label` 控制項，直到所有儲存格都已填滿為止。  
  
   > [!NOTE]
   >  如果您貼上的次數太多，則 IDE 會將新資料列加入至 TableLayoutPanel，讓它有位置可以加入新的 Label 控制項。 您可以將它復原。 若要移除新的儲存格，請選擇 Ctrl+Z 鍵，或依序選擇功能表列上的 [編輯] 和 [復原]。  
  
    現在您的表單已配置完成。其外觀應該如下列圖片。  
  
    ![初始配對遊戲表單](../ide/media/express-tut4step1.png "Express_Tut4Step1")  
   初始配對遊戲表單  
  
### <a name="to-continue-or-review"></a>若要繼續或檢視  
  
-   若要移到下一個教學課程步驟，請參閱[步驟 2：新增隨機物件和圖示清單](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)。  
  
-   若要回到概觀主題，請參閱[教學課程 3：建立配對遊戲](../ide/tutorial-3-create-a-matching-game.md)。



