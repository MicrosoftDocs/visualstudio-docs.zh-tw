---
title: "如何：連接至服務中的資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "資料 [Visual Studio], 連接至 Web 服務"
  - "資料 [Visual Studio], 從 Web 服務讀取"
  - "資料來源, 從 Web 服務建立"
  - "讀取資料, 來自 Web 服務"
  - "Web 服務, 當做資料來源"
  - "Web 服務, 連接"
  - "Web 服務, 讀取資料"
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 32
caps.handback.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：連接至服務中的資料
您可以執行[資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)，並選取 \[**選擇資料來源類型**\] 頁面上的 \[**服務**\]，將應用程式連接到服務傳回的資料。  
  
 完成精靈時，服務參考隨即加入至專案，並且出現在[資料來源視窗](../Topic/Data%20Sources%20Window.md)中。  
  
> [!NOTE]
>  \[**資料來源**\] 視窗中出現的項目需視服務所傳回的資訊而定。  某些服務可能不會提供足夠的資訊，讓 \[**資料來源組態精靈**\] 建立可繫結的物件。  例如，如果服務傳回不具型別的資料集，則完成精靈之後，不會有任何項目出現在 \[**資料來源**\] 視窗中。  這是因為不具型別的資料集不會提供結構描述，所以精靈沒有充分資訊來建立資料來源。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### 若要將應用程式連接至服務  
  
1.  在 \[**資料**\] 功能表上，請按一下 \[**加入新資料來源**\]。  
  
2.  選取 \[**選擇資料來源類型**\] 頁面上的 \[**服務**\]，再按 \[**下一步**\]。  
  
3.  輸入要使用之服務的位址，或按一下 \[**探索**\] 在目前方案中尋找服務，然後按一下 \[**移至**\]。  
  
4.  選擇性地輸入新的 \[**命名空間**\] 以取代預設值。  
  
    > [!NOTE]
    >  按一下 \[**進階**\] 開啟[設定服務參考對話方塊](../data-tools/configure-service-reference-dialog-box.md)。  
  
5.  按一下 \[**確定**\] 將服務參考加入至專案。  
  
6.  按一下 \[**完成**\]。  
  
     此資料來源會加入至 \[**資料來源**\] 視窗中。  
  
## 後續步驟  
  
#### 若要在應用程式中加入功能  
  
-   在 \[**資料來源**\] 視窗中選取任一項目，然後將其拖曳到表單上，以建立繫結控制項。  如需詳細資訊，請參閱[將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
## 請參閱  
 [逐步解說：將 WPF 控制項繫結至 WCF 資料服務](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [逐步解說：將 Silverlight 控制項繫結至 WCF 資料服務](../Topic/Walkthrough:%20Binding%20Silverlight%20Controls%20to%20a%20WCF%20Data%20Service.md)   
 [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)