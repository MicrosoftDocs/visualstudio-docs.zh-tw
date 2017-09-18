---
title: "將 Windows Form 控制項繫結至 Visual Studio 中的資料 | Microsoft Docs"
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
  - "資料 [Windows Form], 資料來源"
  - "資料 [Windows Form], 顯示"
  - "資料來源, 顯示資料"
  - "顯示表單上的資料"
  - "顯示資料, Windows Form"
  - "表單, 顯示資料"
  - "Windows Form, 資料繫結"
  - "Windows Form, 顯示資料"
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 37
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將 Windows Form 控制項繫結至 Visual Studio 中的資料
您可以透過將資料繫結至 Windows Form，對應用程式的使用者顯示資料。  若要建立這些資料繫結控制項，您可以從 \[**資料來源**\] 視窗將項目拖曳至 Visual Studio 中的 Windows Form 設計工具。  本主題描述建立資料繫結 Windows Form 應用程式相關的一些最常用工作、工具和類別。  
  
 如需如何在 Visual Studio 中建立資料繫結控制項的一般資訊，請參閱[將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。  如需 Windows Form 資料繫結的詳細資訊，請參閱 [Windows Form 資料繫結](../Topic/Windows%20Forms%20Data%20Binding.md)。  
  
## 與在 Windows 應用程式之表單上顯示資料有關的工作  
 下表列出與 Windows 應用程式的表單上顯示資料相關的一般工作。  
  
|工作|詳細資訊|  
|--------|----------|  
|建立資料繫結控制項。<br /><br /> 將現有控制項繫結至資料。|[如何：將 Windows Form 控制項繫結至資料](../data-tools/bind-windows-forms-controls-to-data.md)|  
|建立可顯示父子關係中相關資料的控制項：當使用者選取某個控制項中的資料記錄時，另一個控制項會顯示選取之記錄的相關資料。|[如何：在 Windows Form 應用程式中顯示相關的資料](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)|  
|建立「*查閱資料表*」\(Lookup Table\)。  查閱資料表是根據另一個資料表中的外部索引鍵欄位值，顯示某個資料表的資訊。|[如何：在 Windows Form 應用程式中建立查閱資料表](../data-tools/create-lookup-tables-in-windows-forms-applications.md)|  
|將控制項顯示資料的方式格式化。|[Formatting and Advanced Binding Dialog Box](http://msdn.microsoft.com/zh-tw/42638120-9e6f-436b-985f-4036664230fd)|  
|變更 \[**資料來源**\] 視窗中智慧型標題功能的行為。|[如何：自訂 Visual Studio 為資料繫結的控制項建立標題的方式](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|  
|加入執行參數型查詢的控制項。|[如何：將參數型查詢加入至 Windows Form 應用程式](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md)|  
|設定資料行來使用影像控制，以顯示資料庫中的影像。|[如何：從資料庫將控制項繫結至圖片](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
|篩選或排序資料集中的資料。|[如何：在 Windows Form 應用程式中篩選和排序資料](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|  
  
 下列主題提供將 Windows Form 控制項繫結至資料的範例。  
  
 [逐步解說：顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)  
 提供有關查詢資料庫中的資料以及將資料顯示在 Windows Form 上的逐步細節。  
  
 [逐步解說：顯示 Windows Form 上的相關資料](../Topic/Walkthrough:%20Displaying%20Related%20Data%20on%20a%20Windows%20Form.md)  
 提供有關顯示兩個關聯資料表中的資料以及將資料顯示在 Windows Form 上的逐步細節。  
  
 [逐步解說：建立 Windows Form 以搜尋資料](../data-tools/create-a-windows-form-to-search-data.md)  
 提供逐步詳細資訊，說明如何建立 Windows Form，根據使用者輸入來執行資料庫搜尋。  
  
 [逐步解說：在 Windows Form 應用程式中建立查閱資料表](../Topic/Walkthrough:%20Creating%20a%20Lookup%20Table%20in%20a%20Windows%20Forms%20Application.md)  
 提供逐步詳細資訊，說明根據某一個資料表中所選的資料，來顯示另一個資料表中的資料。  
  
 [逐步解說：在 Windows Form 之間傳遞資料](../data-tools/pass-data-between-forms.md)  
 提供逐步詳細資訊，說明如何在應用程式的表單之間傳遞值。  
  
 [逐步解說：建立支援簡單資料繫結的 Windows Form 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)  
 提供有關如何建立可以在 \[**資料來源**\] 視窗中使用之自訂控制項的逐步詳細資料。  
  
 [逐步解說：建立支援複雜資料繫結的 Windows Form 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)  
 提供有關如何建立可以在 \[**資料來源**\] 視窗中使用之自訂控制項的逐步詳細資料。  
  
 [逐步解說：建立支援查閱資料繫結的 Windows Form 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)  
 提供有關如何建立可以在 \[**資料來源**\] 視窗中使用之自訂控制項的逐步詳細資料。  
  
## 資料智慧標籤  
 許多控制項有專門處理資料的智慧標籤。  特定控制項加入至表單時，智慧標籤上會有一組與資料相關的可能動作。  
  
## BindingSource 元件  
 <xref:System.Windows.Forms.BindingSource> 元件有兩個用途。  第一，將表單上的控制項繫結至資料時，它提供抽象層。  表單上的控制項會繫結至 <xref:System.Windows.Forms.BindingSource> 元件 \(而不是直接繫結至資料來源\)。  
  
 第二，它可以管理物件的集合。  將某個型別加入至 <xref:System.Windows.Forms.BindingSource>，會建立該型別清單。  
  
 如需 <xref:System.Windows.Forms.BindingSource> 元件的詳細資訊，請參閱：  
  
-   [BindingSource 元件](../Topic/BindingSource%20Component.md)  
  
-   [BindingSource 元件概觀](../Topic/BindingSource%20Component%20Overview.md)  
  
-   [BindingSource 元件架構](../Topic/BindingSource%20Component%20Architecture.md)  
  
## BindingNavigator 控制項  
 這個元件提供巡覽 Windows 應用程式所顯示之資料的使用者介面。  如需詳細資訊，請參閱[BindingNavigator 控制項](../Topic/BindingNavigator%20Control%20\(Windows%20Forms\).md)。  
  
## DataGridView 控制項  
 <xref:System.Windows.Forms.DataGridView> 控制項讓您顯示和編輯來自各種不同資料來源的表格式資料。  您可以使用 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 屬性將資料繫結至 <xref:System.Windows.Forms.DataGridView>。  如需詳細資訊，請參閱[DataGridView 控制項概觀](../Topic/DataGridView%20Control%20Overview%20\(Windows%20Forms\).md)。  
  
## 請參閱  
 [資料逐步解說](../Topic/Data%20Walkthroughs.md)   
 [資料來源視窗](../Topic/Data%20Sources%20Window.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [逐步解說：顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)   
 [資料來源概觀](../data-tools/add-new-data-sources.md)   
 [逐步解說：建立支援簡單資料繫結的 Windows Form 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)   
 [逐步解說：建立支援複雜資料繫結的 Windows Form 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)   
 [逐步解說：建立支援查閱資料繫結的 Windows Form 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)