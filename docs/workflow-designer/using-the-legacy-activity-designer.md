---
title: "使用舊版活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "活動, 新增子系"
  - "活動, 設定"
  - "活動, 建立自訂"
  - "活動設計工具"
  - "子活動, 新增"
  - "自訂活動"
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 使用舊版活動設計工具
本主題描述如何在舊版 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中使用活動設計工具。當以 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 為目標時，請使用舊版設計工具。  
  
 活動設計工具可讓您建立自訂活動。  
  
## 建立自訂活動  
 依照下列步驟使用活動設計工具建立自訂活動：  
  
1.  在 \[**專案**\] 功能表上，按一下 \[**新增活動**\]。  
  
2.  選取 \[**活動**\] 或 \[**活動 \(程式碼分開置放\)**\] 範本。  
  
    1.  使用 \[**活動**\] 範本，以相同程式碼檔案中的活動定義和使用者程式碼來建立活動。  
  
    2.  使用 \[**活動 \(程式碼分開置放\)**\] 範本，使用不同程式碼檔案中的使用者程式碼和表示為工作流程標記的活動定義來建立活動。  
  
3.  輸入活動名稱或保留預設名稱，再按一下 \[**新增**\]。  
  
 您也可以建立 **Workflow Activity Library** 類型的新專案來建立一組自訂的活動。如需這個專案類型的詳細資訊，請參閱[HOW TO：建立工作流程活動程式庫 \(舊版\)](../Topic/How%20to:%20Create%20a%20Workflow%20Activity%20Library%20\(Legacy\).md)。  
  
## 設定活動  
 活動設計工具為使用中時，可使用屬性瀏覽器設定下表所列的屬性。  
  
|屬性|註解|  
|--------|--------|  
|**Name**|活動名稱。|  
|**Base Class**|衍生活動的基底類別。預設的基底類別為 [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020) \(本頁面可能為英文\)。在 \[**屬性**\] 視窗中，按一下 \[**基底類別**\] 省略符號 **\[…\]**，選取[瀏覽並選取 .NET 類型對話方塊 \(舊版\)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)中其他的基底類別。|  
|**Description**|使用者定義的活動描述。|  
|**Enabled**|預設值為 **True**，以啟用活動的執行與驗證。設為 **False** 會停用活動的執行與驗證。如需活動執行和驗證的詳細資訊，請參閱[開發工作流程活動](http://go.microsoft.com/fwlink?LinkID=65024) \(英文\)。|  
  
## 新增子活動  
 您可以將子活動從 \[工具箱\] 拖曳至您正在設計的活動。接著，便可以使用屬性瀏覽器設定每一個子活動。  
  
## 請參閱  
 [開發工作流程活動](http://go.microsoft.com/fwlink?LinkID=65024)   
 [建立自訂活動](http://go.microsoft.com/fwlink?LinkID=65021)   
 [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)   
 [自訂活動範例](http://go.microsoft.com/fwlink?LinkID=65022)   
 [HOW TO：建立工作流程活動程式庫 \(舊版\)](../Topic/How%20to:%20Create%20a%20Workflow%20Activity%20Library%20\(Legacy\).md)   
 [使用舊版工作流程設計工具](../workflow-designer/using-the-legacy-workflow-designer.md)