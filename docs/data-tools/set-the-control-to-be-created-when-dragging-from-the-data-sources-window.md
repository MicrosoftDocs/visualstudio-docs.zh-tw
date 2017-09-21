---
title: "設定從 [資料來源] 視窗拖曳時要建立的控制項 | Microsoft Docs"
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
  - "資料來源視窗, 選取控制項"
  - "Windows Forms, 顯示資料"
  - "資料 [Visual Studio], 在 Windows Forms 上顯示"
  - "資料 [Visual Studio], [資料來源] 視窗"
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
caps.latest.revision: 31
caps.handback.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 設定從 [資料來源] 視窗拖曳時要建立的控制項
您可以從 \[**資料來源**\] 視窗將項目拖曳至 WPF 設計工具或 Windows Form 設計工具中，以建立資料繫結控制項。  在 \[**資料來源**\] 視窗中，每個項目都會有一個您將項目拖曳到設計工具時建立的預設控制項。  但您也可以選擇建立不同的控制項。  
  
## 設定要為資料表或物件建立的控制項  
 從 \[**資料來源**\] 視窗拖曳表示資料表或物件的項目之前，您可以選擇在一個控制項中顯示所有資料，還是在個別控制項中顯示每個資料行或屬性。  
  
 在此內容中，「*物件*」\(Object\) 一詞是指自訂商務物件、實體 \(在實體資料模型中\) 或服務傳回的物件。  
  
#### 若要設定要為資料表或物件建立的控制項  
  
1.  確定 WPF 設計工具或 Windows Form 設計工具是開啟的。  
  
2.  在 \[**資料來源**\] 視窗中，選取表示要設定之資料表或物件的項目。  
  
3.  按一下項目的下拉式功能表，然後按一下功能表中的下列一項：  
  
    -   若要在個別控制項中顯示每個資料欄位，請按一下 \[**詳細資料**\]。  當您將資料項目拖曳至設計工具時，這個動作會為父資料表或物件的每個資料行或屬性建立不同的資料繫結控制項，以及每個控制項的標題。  
  
    -   若要在單一控制項中顯示所有資料，請在清單中選取不同的控制項，例如 WPF 應用程式中的 \[**DataGrid**\] 或 \[**List**\]，或是 Windows Form 應用程式中的 \[**DataGridView**\]。  
  
     可用控制項的清單取決於已開啟的設計工具、專案的 .NET Framework 目標版本，以及您是否已經將支援資料繫結的自訂控制項加入至 \[**工具箱**\]。  如果您要建立的控制項位於可用控制項清單中，就可以將該控制項加入至清單。  如需詳細資訊，請參閱[將自訂控制項加入 \[資料來源\] 視窗](../Topic/Add%20custom%20controls%20to%20the%20Data%20Sources%20window.md)。  
  
     若要了解如何建立可加入至 \[**資料來源**\] 視窗中資料表或物件之控制項清單的自訂 Windows Form 控制項，請參閱[逐步解說：建立支援複雜資料繫結的 Windows Form 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)。  
  
## 設定要為資料行或屬性建立的控制項  
 從 \[**資料來源**\] 視窗將表示資料行或物件屬性的項目拖曳至設計工具之前，您可以設定要建立的控制項。  
  
#### 若要設定要為資料行或屬性建立的控制項  
  
1.  確定 WPF 設計工具或 Windows Form 設計工具是開啟的。  
  
2.  在 \[**資料來源**\] 視窗中，展開所要的資料表或物件，以顯示其資料行或屬性。  
  
3.  選取您要為其建立控制項的每個資料行或屬性。  
  
4.  按一下資料行或屬性的下拉式功能表，然後選取將項目拖曳到設計工具時要建立的控制項。  
  
     可用控制項的清單取決於已開啟的設計工具、專案的 .NET Framework 目標版本，以及已加入至 \[**工具箱**\] 中支援資料繫結的自訂控制項。  如果您要建立的控制項位於可用控制項清單中，就可以將該控制項加入至清單。  如需詳細資訊，請參閱[將自訂控制項加入 \[資料來源\] 視窗](../Topic/Add%20custom%20controls%20to%20the%20Data%20Sources%20window.md)。  
  
     若要了解如何建立可加入至 \[**資料來源**\] 視窗中資料行或屬性之控制項清單的自訂控制項，請參閱[逐步解說：建立支援簡單資料繫結的 Windows Form 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)。  
  
     如果您不要為資料行或屬性建立控制項，請選取下拉式功能表中的 \[**無**\]。  如果您要將父資料表或物件拖曳至設計工具中，但不要包含特定資料行或屬性時，這會非常有用。  
  
## 請參閱  
 [資料逐步解說](../Topic/Data%20Walkthroughs.md)   
 [逐步解說：顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)   
 [資料來源概觀](../data-tools/add-new-data-sources.md)   
 [資料來源視窗](../Topic/Data%20Sources%20Window.md)   
 [將自訂控制項加入 \[資料來源\] 視窗](../Topic/Add%20custom%20controls%20to%20the%20Data%20Sources%20window.md)