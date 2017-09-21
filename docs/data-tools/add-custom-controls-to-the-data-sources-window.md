---
title: "將自訂控制項加入 [資料來源] 視窗 | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.howtoaddcustomcontrol"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "資料來源視窗, 加入控制項"
  - "控制項 [Visual Studio], 加入資料來源視窗"
  - "DefaultBindingPropertyAttribute 類別, 使用"
  - "LookupBindingPropertiesAttribute 類別, 使用"
  - "ComplexBindingPropertiesAttribute 類別, 使用"
  - "資料來源視窗, 選取控制項"
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
caps.latest.revision: 42
caps.handback.revision: 39
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將自訂控制項加入 [資料來源] 視窗
當您從 \[**資料來源**\] 視窗將項目拖曳至設計介面以建立資料繫結控制項時，可以選取要建立的控制項型別。  在視窗中的每個項目都有下拉式清單，顯示可選擇的控制項。  每個項目的關聯控制項集合是由項目的資料型別所決定。  如果您要建立的控制項未出現在清單中，可以依照本主題中的指示，將控制項加入至清單。  
  
 如需選取資料繫結控制項，為 \[**資料來源**\] 視窗中的項目建立這些控制項的詳細資訊，請參閱 [設定從 \[資料來源\] 視窗拖曳時要建立的控制項](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請選取 \[**工具**\] 功能表上的 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
##  <a name="customizinglist"></a> 自訂資料型別的可繫結控制項清單  
 執行下列步驟，對 \[**資料來源**\] 視窗中有特定資料型別之項目的可用控制項清單加入或移除控制項。  
  
#### 若要選取針對資料型別列出的控制項  
  
1.  確定 WPF 設計工具或 Windows Form 設計工具是開啟的。  
  
2.  在 \[**資料來源**\] 視窗中，按一下屬於已加入至視窗中之資料來源一部分的項目，然後按一下此項目的下拉式功能表。  
  
3.  按一下下拉式功能表中的 \[**自訂**\]。  下列其中一個對話方塊隨即開啟：  
  
    -   如果 Windows Form 設計工具已開啟，則會開啟 \[**選項**\] 對話方塊的 \[**自訂資料欄位 UI**\] 頁面。  
  
    -   如果 WPF 設計工具已開啟，則會開啟 \[**自訂控制繫結**\] 對話方塊。  
  
4.  在對話方塊中，從 \[**資料型別**\] 下拉式清單中選取資料型別。  
  
    -   若要自訂資料表或物件的控制項清單，請選取 \[**清單**\]。  
  
    -   若要自訂資料表資料行或物件屬性的控制項清單，請選取基礎資料存放區中資料行或屬性的資料型別。  
  
    -   若要自訂控制項清單以顯示具有使用者定義圖案的資料物件，請選取 \[**其他**\]。  例如，如果應用程式有自訂控制項，而這個控制項顯示某個物件中一個以上的屬性資料時，請選取 \[**其他**\]。  
  
5.  在 \[**關聯的控制項**\] 方塊中，選取要用於所選取資料型別的每一個控制項，或取消選取要從清單中移除的任何控制項。  
  
    > [!NOTE]
    >  如果您要選取的控制項未出現在 \[**關聯的控制項**\] 方塊中，必須將控制項加入至清單。  如需詳細資訊，請參閱[將控制項加入至資料型別的關聯控制項清單](#addingcontrols)。  
  
6.  按一下 \[**確定**\]。  
  
7.  在 \[**資料來源**\] 視窗中，按一下您剛才與一個或多個控制項相關聯之資料型別的項目，然後按一下此項目的下拉式功能表。  
  
     您在 \[**關聯的控制項**\] 方塊中選取的控制項，現在會出現在項目的下拉式功能表中。  
  
##  <a name="addingcontrols"></a> 將控制項加入至資料型別的關聯控制項清單  
 如果您要將控制項與資料型別產生關聯，但該控制項未出現在 \[**關聯的控制項**\] 方塊中，必須將控制項加入至清單。  控制項必須位於目前方案或參考的組件中、是 \[**工具箱**\] 中的可用控制項，並且有指定控制項資料繫結行為的屬性。  
  
#### 若要將控制項加入至關聯的控制項清單  
  
1.  在 \[**工具箱**\] 上按一下滑鼠右鍵，並選取 \[**選擇項目**\]，將所要的控制項加入至 \[**工具箱**\]。  
  
     控制項必須有下列其中一個屬性。  
  
    |屬性|描述|  
    |--------|--------|  
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|在顯示單一資料行 \(或屬性\) 的簡單控制項上實作這個屬性，例如 <xref:System.Windows.Forms.TextBox>。|  
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|在顯示資料清單 \(或資料表\) 的控制項上實作這個屬性，例如 <xref:System.Windows.Forms.DataGridView>。|  
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|在顯示資料清單 \(或資料表\)，但需要呈現單一資料行或屬性的控制項上實作這個屬性，例如 <xref:System.Windows.Forms.ComboBox>。|  
  
2.  開啟 \[**選項**\] 對話方塊的 \[**自訂資料欄位 UI**\] 頁面 \(適用於 Windows Form\)，或開啟 \[**自訂控制繫結**\] 對話方塊 \(適用於 WPF\)。  如需詳細資訊，請參閱[自訂資料型別的可繫結控制項清單](#customizinglist)。  
  
3.  剛才加入至 \[**工具箱**\] 的控制項，現在應該會出現在 \[**關聯的控制項**\] 方塊中。  
  
    > [!NOTE]
    >  只有位在目前方案或參考的組件中的控制項 \(以及實作上表的其中一個資料繫結屬性的控制項\) 才可以加入到關聯控制項的清單中。  若要將資料繫結至不在 \[**資料來源**\] 視窗中的自訂控制項，請將此控制項從 \[**工具箱**\] 拖曳至設計介面，然後將要繫結的項目從 \[**資料來源**\] 視窗拖曳至控制項。  
  
## 請參閱  
 [逐步解說：顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)   
 [資料來源概觀](../data-tools/add-new-data-sources.md)   
 [設定從 \[資料來源\] 視窗拖曳時要建立的控制項](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)   
 [逐步解說：建立支援簡單資料繫結的 Windows Form 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)   
 [逐步解說：建立支援複雜資料繫結的 Windows Form 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)   
 [逐步解說：建立支援查閱資料繫結的 Windows Form 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)   
 [自訂控制項繫結對話方塊](../data-tools/customize-control-binding-dialog-box.md)