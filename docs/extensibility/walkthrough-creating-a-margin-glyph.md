---
title: "逐步解說︰ 建立邊界圖像 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，新的邊界圖像"
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# 逐步解說︰ 建立邊界圖像
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用自訂的編輯器延伸模組，您可以自訂編輯器邊界的外觀。 本逐步解說中放置自訂圖像的指標邊界，每當"todo"這個字出現在程式碼註解。  
  
## 必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 建立 MEF 專案  
  
1.  建立 C\# VSIX 專案。 \(在 **新的專案** 對話方塊中，選取 **Visual C\# \/ 擴充性**, ，然後 **VSIX 專案**。\) 將方案命名為 `TodoGlyphTest`。  
  
2.  加入分類編輯器專案項目。 如需詳細資訊，請參閱[使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  刪除現有類別檔案。  
  
## 定義圖像 （glyph）  
 藉由實作定義圖像 （glyph） <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> 介面。  
  
#### 若要定義圖像 （glyph）  
  
1.  將類別檔案，並將它 `TodoGlyphFactory`。  
  
2.  新增下列使用宣告。  
  
     [!code-cs[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  新增名為 `TodoGlyphFactory` 實作 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>。  
  
     [!code-cs[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  加入私用欄位來定義維度的圖像。  
  
     [!code-cs[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  實作 `GenerateGlyph` 藉由定義圖像 （glyph） 使用者介面 \(UI\) 項目。`TodoTag` 本逐步解說稍後定義。  
  
     [!code-cs[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  新增名為 `TodoGlyphFactoryProvider` 實作 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>。 匯出與這個類別 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 的 「 TodoGlyph 」， <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> 之後 VsTextMarker 的 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 的 「 程式碼 」 和 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag。  
  
     [!code-cs[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  實作 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> 方法具現化 `TodoGlyphFactory`。  
  
     [!code-cs[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## 定義 Todo 標記與標註器  
 藉由建立標記型別與標註器，並將它匯出使用標註器提供者定義的指標邊界，在先前步驟中所定義的 UI 項目之間的關聯性。  
  
#### 若要定義 todo 標記和標註器  
  
1.  將新的類別檔案加入至專案，並將它 `TodoTagger`。  
  
2.  新增下列匯入。  
  
     [!code-cs[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  新增名為 `TodoTag`。  
  
     [!code-cs[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  修改類別，名為 `TodoTagger` 實作 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 型別的 `TodoTag`。  
  
     [!code-cs[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  若要 `TodoTagger` 類別，加入私用欄位的 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 和文字，以尋找該分類中的擴展。  
  
     [!code-cs[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  新增設定分類器的建構函式。  
  
     [!code-cs[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  實作 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 方法藉由尋找所有分類涵蓋其名稱包含單字"註解 」，以及其文字包含搜尋文字。 找到搜尋文字，只要重新產生新 <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> 型別的 `TodoTag`。  
  
     [!code-cs[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  宣告 `TagsChanged` 事件。  
  
     [!code-cs[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. 新增名為 `TodoTaggerProvider` 實作 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, ，並將它與匯出 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 的 「 程式碼 」 和 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag。  
  
     [!code-cs[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. 匯入 <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>。  
  
     [!code-cs[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. 實作 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> 方法具現化 `TodoTagger`。  
  
     [!code-cs[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## 建置和測試程式碼  
 若要測試這段程式碼，TodoGlyphTest 方案中建置並執行它的實驗執行個體。  
  
#### 若要建置和測試 TodoGlyphTest 方案  
  
1.  建置方案。  
  
2.  按 F5 執行專案。 Visual Studio 的第二個執行個體具現化。  
  
3.  請確定會顯示指標邊界。 \(在 **工具** \] 功能表上，按一下 \[ **選項**。 在 **文字編輯器** 頁面上，請確定 **指標邊界** 已選取。\)  
  
4.  開啟有註解的程式碼檔案。 將"todo"這個字加入至其中一個註解區段。  
  
5.  深藍色外框的淺藍色圓形應該會出現在左邊的 \[程式碼\] 視窗的指標邊界。