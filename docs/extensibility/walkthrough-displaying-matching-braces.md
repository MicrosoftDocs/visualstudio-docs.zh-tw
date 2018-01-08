---
title: "逐步解說： 顯示對稱的括號 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c3dde61c10d0a8c9fc5578b02cc713f648409cbf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-displaying-matching-braces"></a>逐步解說： 顯示對稱的括號
您可以實作語言為基礎的功能，例如定義您想要比對，在大括的號，然後將文字標記標記加入至對稱的括號，當插入號位於其中一個大括號比對的大括號。 您可以定義大括號中的內容語言，或您可以定義您自己的檔案名稱副檔名和內容類型，並將標籤套用到僅該型別，或您可以將標籤套用到現有的內容類型 （例如"text")。 下列逐步解說示範如何套用至"text"的內容類型的標籤進行比對括號。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>建立 MEF 專案  
  
1.  建立編輯器分類器專案。 將方案命名`BraceMatchingTest`。  
  
2.  編輯器分類器項目範本加入專案。 如需詳細資訊，請參閱[編輯器項目範本以建立擴充](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  刪除現有類別檔案。  
  
## <a name="implementing-a-brace-matching-tagger"></a>實作大括號比對標記者  
 若要取得類似使用 Visual Studio 中的效果反白顯示在括號，您可以實作的類型的標記者<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>。 下列程式碼會示範如何定義任何層級的巢狀大括號組標記。 在此範例中，大括號組 []。 [] {} 中的標記者建構函式，定義，但在完整的語言實作相關的大括號組應該定義語言規格中。  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>若要實作大括號比對標記者  
  
1.  將類別檔案並將它命名為 BraceMatching。  
  
2.  匯入下列命名空間。  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  定義類別`BraceMatchingTagger`繼承自<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>型別的<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>。  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  加入屬性的文字檢視、 來源緩衝區，和目前的快照集點，以及一組括號組。  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  在標記者建構函式，設定屬性和訂閱檢視變更事件<xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged>和<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>。 在此範例中，為方便說明，對稱的括號中也會定義建構函式。  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  做為一部分<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>實作中，宣告 TagsChanged 事件。  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  事件處理常式更新目前插入號位置的`CurrentChar`屬性並且引發 TagsChanged 事件。  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  實作<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>方法來比對括號是時的目前字元是左大括號或前一個字元時關閉的大括號，如 Visual Studio 所示。 找到相符項目時，這個方法具現化，兩個標記，一個用於左大括號，一個用於關閉的大括號。  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. 下列的私用方法尋找在任何層級的巢狀對稱的括號。 第一種方法會找出符合開啟字元關閉字元：  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. 下列 helper 方法會找出開啟符合關閉字元的字元：  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>實作大括號比對標記者提供者  
 除了實作的標記者，您也必須實作並匯出標記者提供者。 在此情況下，提供者的內容類型為"text"。 這表示比對括號會出現在所有類型的文字檔案，但更完整的實作適用於大括號比只對特定的內容類型。  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>若要實作的大括號比對標記者提供者  
  
1.  宣告的標記者提供者，繼承自<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>、 BraceMatchingTaggerProvider，將它命名，並將它與匯出<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>的 「 文字 」 和<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>的<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>。  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  實作<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>BraceMatchingTagger 具現化的方法。  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## <a name="building-and-testing-the-code"></a>建置和測試程式碼  
 若要測試這段程式碼，建置 BraceMatchingTest 方案，並在實驗執行個體中執行。  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>若要建置和測試 BraceMatchingTest 方案  
  
1.  建置方案。  
  
2.  當您在偵錯工具中執行這個專案時，會具現化第二個 Visual Studio 執行個體。  
  
3.  建立文字檔案，並輸入一些文字，其中包含對稱的括號。  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  當您開啟的大括號前面插入號時，該括號和關閉對稱的大括號應該會反白顯示。 當您將游標放只在關閉的大括號之後時，該括號和相符的左大括號應該會反白顯示。  
  
## <a name="see-also"></a>請參閱  
 [逐步解說︰將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)