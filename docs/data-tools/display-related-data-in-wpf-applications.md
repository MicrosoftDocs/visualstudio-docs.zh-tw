---
title: "如何：在 WPF 應用程式中顯示相關的資料 | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "資料 [WPF], 顯示"
  - "資料繫結, WPF"
  - "顯示資料, WPF"
  - "WPF [WPF], 資料"
  - "WPF 資料繫結 [Visual Studio]"
  - "WPF Designer, 資料繫結"
  - "WPF, Visual Studio 中的資料繫結"
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在 WPF 應用程式中顯示相關的資料
在某些應用程式中，您可以處理來自彼此為父子關係之多個相關資料表或實體的資料。  例如，您可能會想要在格線中顯示來自 `Customers` 資料表的客戶。  當使用者選取特定客戶時，另一個格線會從相關 `Orders` 資料表中顯示該客戶的訂單。  
  
 您可以從 \[**資料來源**\] 視窗將項目拖曳至 WPF 設計工具中，以建立顯示相關資料的資料繫結控制項。  
  
### 建立顯示相關資料錄的控制項  
  
1.  在 \[**資料**\] 功能表上按一下 \[**顯示資料來源**\]，以開啟 \[**資料來源**\] 視窗。  
  
2.  按一下 \[**加入新資料來源**\]，並完成 \[**資料來源組態精靈**\]。  
  
3.  開啟 WPF 設計工具，並確定設計工具包含的容器是 \[**資料來源**\] 視窗中項目的有效置放目標。  
  
     如需有效置放目標的詳細資訊，請參閱[將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
4.  在 \[**資料來源**\] 視窗中，展開表示關聯性父資料表或物件的節點。  父資料表或物件位於一對多關聯性的「一」方。  
  
5.  從 \[**資料來源**\] 視窗將父節點 \(或父節點中的任何個別項目\) 拖曳至設計工具中的有效置放目標。  
  
     Visual Studio 會針對您拖曳的每個項目產生建立新資料繫結控制項的 XAML。  XAML 也會將父資料表或物件的新 <xref:System.Windows.Data.CollectionViewSource> 加入置放目標的資源中。  對於某些資料來源，Visual Studio 也會產生可將資料載入父資料表或物件中的程式碼。  如需詳細資訊，請參閱[將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
6.  在 \[**資料來源**\] 視窗中，尋找相關的子資料表或物件。  相關子資料表和物件會出現在父節點的資料清單底端，做為可展開節點。  
  
7.  從 \[**資料來源**\] 視窗將子節點 \(或子節點中的任何個別項目\) 拖曳至設計工具中的有效置放目標。  
  
     Visual Studio 會針對您拖曳的每個項目產生建立新資料繫結控制項的 XAML。  XAML 也會將子資料表或物件的新 <xref:System.Windows.Data.CollectionViewSource> 加入置放目標的資源中。  這個新 <xref:System.Windows.Data.CollectionViewSource> 會繫結至您剛拖曳至設計工具中之父資料表或物件的屬性。  對於某些資料來源，Visual Studio 也會產生可將資料載入子資料表或物件中的程式碼。  
  
     下圖示範 \[**資料來源**\] 視窗中資料集之 \[**Customers**\] 資料表的相關 \[**Orders**\] 資料表。  
  
     ![顯示關聯的資料來源視窗](~/data-tools/media/datasources2.gif "DataSources2")  
  
## 請參閱  
 [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [如何：將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [如何：利用 WPF 應用程式建立查閱資料表](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [逐步解說：顯示 WPF 應用程式中的相關資料](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)