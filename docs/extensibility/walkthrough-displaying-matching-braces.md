---
title: "逐步解說︰ 顯示對稱的括號 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，新的括號對稱"
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# 逐步解說︰ 顯示對稱的括號
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以實作語言為基礎的功能，例如括號對稱定義您想要比對，大括的號，然後將文字標記標記加入至對稱的括號時插入號是大括號的其中一個。 您可以定義大括號內的一種語言，您可以定義您的檔案名稱副檔名和內容類型，並將標籤套用到只是該型別，或您可以將標籤套用到現有的內容類型 （例如 「 文字 」）。 下列逐步解說示範如何套用到 「 文字 」 內容類型的標籤進行比對括號。  
  
## 必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## Managed Extensibility Framework \(MEF\)  
  
#### 建立 MEF 專案  
  
1.  建立編輯器分類器專案。 將方案命名為 `BraceMatchingTest`。  
  
2.  將編輯器分類項目範本加入至專案。 如需詳細資訊，請參閱[使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  刪除現有類別檔案。  
  
## 實作括號對稱標註器  
 若要取得一個大括號反白顯示類似使用 Visual Studio 中的效果，您可以實作型別的標註器 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>。 下列程式碼示範如何定義的任何層級的巢狀大括號組標註器。 在此範例中，大括號組 \[\]。 \[\] {} 定義在標註器建構函式，而在完整的語言實作相關的大括號配對會定義語言規格中。  
  
#### 若要實作的括號對稱標註器  
  
1.  將類別檔案，並將它括號對稱。  
  
2.  匯入下列命名空間。  
  
     [!code-cs[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  定義類別 `BraceMatchingTagger` 繼承自 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 型別的 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>。  
  
     [!code-cs[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  加入屬性的文字檢視中，來源緩衝區，和目前的快照集點，以及一組大括號組。  
  
     [!code-cs[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  標註器建構函式中設定屬性，並檢視變更事件訂閱 <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> 和 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>。 在此範例中，為方便說明，對稱的括號中也會定義建構函式。  
  
     [!code-cs[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  一部分 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 實作中，宣告 TagsChanged 事件。  
  
     [!code-cs[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  事件處理常式更新目前插入號位置的 `CurrentChar` 屬性並引發 TagsChanged 事件。  
  
     [!code-cs[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  實作 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 方法來比對括號是當目前字元是左大括號或前一個字元時關閉的大括號，如 Visual Studio 所示。 找到相符項目時，這個方法具現化，這兩個標籤、 一個左大括號和一個右大括弧。  
  
     [!code-cs[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. 下列的私用方法尋找在任何層級的巢狀對稱的括號。 第一種方法會尋找符合開啟字元關閉字元︰  
  
     [!code-cs[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. 下列 helper 方法會尋找開啟符合關閉字元的字元︰  
  
     [!code-cs[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## 實作括號對稱標註器提供者  
 除了實作標註器，您也必須實作並匯出標註器提供者。 在此情況下，提供者的內容類型為"text"。 這表示比對括號會出現在所有類型的文字檔案，但更完整的實作適用於括號對稱僅以特定的內容類型。  
  
#### 若要實作的大括號相符標註器提供者  
  
1.  宣告繼承自標註器提供者 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, 、 將它命名為 BraceMatchingTaggerProvider，並將它與匯出 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 的 「 文字 」 和 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> 的 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>。  
  
     [!code-cs[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  實作 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> BraceMatchingTagger 具現化的方法。  
  
     [!code-cs[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## 建置和測試程式碼  
 若要測試這段程式碼，BraceMatchingTest 方案中建置並執行它的實驗執行個體。  
  
#### 若要建置和測試 BraceMatchingTest 方案  
  
1.  建置方案。  
  
2.  當您在偵錯工具中執行這個專案時，會具現化第二個 Visual Studio 執行個體。  
  
3.  建立文字檔案，並輸入一些文字，其中包含對稱的括號。  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  當您在左大括號之前插入號時，該大括號和關閉對稱的大括號應該會反白顯示。 當您將游標右大括弧之後時，該大括號和相符的左大括號應該會反白顯示。  
  
## 請參閱  
 [逐步解說: 將內容類型連結至檔案名稱副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)