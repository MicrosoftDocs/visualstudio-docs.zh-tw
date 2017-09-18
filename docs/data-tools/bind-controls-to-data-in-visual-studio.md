---
title: "將控制項繫結至 Visual Studio 中的資料 | Microsoft Docs"
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
  - "資料來源視窗"
  - "資料來源, 顯示資料"
  - "資料, 顯示"
  - "顯示資料"
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 40
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將控制項繫結至 Visual Studio 中的資料
您可以透過將資料繫結至控制項，對應用程式的使用者顯示資料。  您可以從 \[**資料來源**\] 視窗將項目拖曳至 Visual Studio 設計介面上，藉以建立這些資料繫結控制項。  
  
 這個主題描述可用來建立資料繫結控制項的資料來源。  此外，也描述與資料繫結相關的一些一般工作。  如需如何建立資料繫結控制項的詳細資訊，請參閱[將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)、[將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)和[將 Silverlight 控制項繫結至 Visual Studio 中的資料](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md)。  
  
## 資料來源  
 資料來源表示應用程式可使用的資料。  您可以從資料庫、服務或物件中建立資料來源。  如需詳細資訊，請參閱[資料來源概觀](../data-tools/add-new-data-sources.md)。  
  
 有些資料來源可讓您從 \[**資料來源**\] 視窗拖曳項目，以建立資料繫結控制項，有些資料來源則否。  下表顯示支援的資料來源。  
  
|資料來源|**Windows Form 設計工具**的拖放支援|**WPF 設計工具**的拖放支援|**Silverlight Designer** 的拖放支援|  
|----------|--------------------------------|-----------------------|------------------------------------|  
|資料集|是|是|否|  
|實體資料模型|否<sup>1</sup>|是|是|  
|LINQ to SQL 類別|否<sup>2</sup>|否<sup>2</sup>|否<sup>2</sup>|  
|服務 \(包括 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]、Web 服務和 Web 服務\)|是|是|是|  
|物件|是|是|是|  
|SharePoint|是|是|是|  
  
 1.  當 \[**Windows Form 設計工具**\] 開啟時，\[**資料來源**\] 視窗中的實體為唯讀，無法拖曳至設計工具。  不過，您仍然可以根據實體資料模型加入新的物件資料來源，然後將這些物件拖曳至設計工具，來建立資料繫結控制項。  
  
 2.  LINQ to SQL 類別不會出現在 \[**資料來源**\] 視窗中。  不過，您可以根據 LINQ to SQL 類別加入新的物件資料來源，然後將這些物件拖曳至設計工具，來建立資料繫結控制項。  如需詳細資訊，請參閱[逐步解說：建立 LINQ to SQL 類別 \(O\/R 設計工具\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)。  
  
## 資料來源視窗  
 資料來源會在 \[**資料來源**\] 視窗中以項目形式使用於專案。  您可以從這個視窗拖曳項目，藉以建立繫結至基礎資料的控制項。  如需詳細資訊，請參閱[資料來源視窗](../Topic/Data%20Sources%20Window.md)。  
  
 對於 \[**資料來源**\] 視窗中的每個資料類型，將項目拖曳到設計工具時都會建立一個預設控制項。  從 \[**資料來源**\] 視窗拖曳項目之前，您可以變更將建立的控制項。  如需詳細資訊，請參閱 [設定從 \[資料來源\] 視窗拖曳時要建立的控制項](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)。  
  
## 將控制項繫結至資料的相關工作  
 下表列出將控制項繫結至資料的一些最常用工作。  
  
|工作|詳細資訊|  
|--------|----------|  
|開啟 \[**資料來源**\] 視窗。|[如何：開啟資料來源視窗](../data-tools/how-to-open-the-data-sources-window.md)|  
|將資源來源加入至專案。|[如何：連接至資料庫中的資料](../data-tools/how-to-connect-to-data-in-a-database.md)<br /><br /> [如何：連接至物件中的資料](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)<br /><br /> [如何：連接至服務中的資料](../data-tools/how-to-connect-to-data-in-a-service.md)|  
|設定當您從 \[**資料來源**\] 視窗中將項目拖曳到設計工具時建立的控制項。|[設定從 \[資料來源\] 視窗拖曳時要建立的控制項](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)|  
|修改與 \[**資料來源**\] 視窗中之項目相關聯的控制項清單。|[將自訂控制項加入 \[資料來源\] 視窗](../Topic/Add%20custom%20controls%20to%20the%20Data%20Sources%20window.md)|  
|建立資料繫結控制項。|[將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)<br /><br /> [將 Silverlight 控制項繫結至 Visual Studio 中的資料](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md)|  
  
 建立繫結至資料的控制項之後，可能需要執行下列其中一個工作。  
  
|工作|詳細資訊|  
|--------|----------|  
|編輯基礎資料來源中的資料|[在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)|  
|驗證資料變更|[驗證資料](../Topic/Validating%20Data.md)|  
|將更新資料儲存回資料庫|[儲存資料](../data-tools/saving-data.md)|  
  
## 請參閱  
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [將 Silverlight 控制項繫結至 Visual Studio 中的資料](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md)   
 [如何：從資料庫將控制項繫結至圖片](../data-tools/bind-controls-to-pictures-from-a-database.md)   
 [Visual Studio 資料應用程式的概觀](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)   
 [用來在 Visual Studio 中使用資料來源的工具](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)