---
title: 逐步解說：顯示成對的大括弧 |Microsoft Docs
description: 瞭解如何使用這個逐步解說，在語言的內容中定義大括弧，並將大括弧比對標記套用至文字內容類型。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce40f5673a8aba4ab3f7714a3aafdc3de4697cc4
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877945"
---
# <a name="walkthrough-display-matching-braces"></a>逐步解說：顯示成對的大括弧
藉由定義您想要比對的大括弧來執行以語言為基礎的功能（例如，大括弧比對），並在插入點位於其中一個大括弧時，將文字標記標記新增至相符的大括弧。 您可以在語言的內容中定義大括弧、定義您自己的副檔名和內容類型，並將標記套用至現有的內容類型， (例如「文字」 ) 。 下列逐步解說示範如何將大括弧比對標記套用至 "text" 內容類型。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-managed-extensibility-framework-mef-project"></a>建立 Managed Extensibility Framework (MEF) 專案

#### <a name="to-create-a-mef-project"></a>建立 MEF 專案

1. 建立編輯器分類器專案。 將方案命名為 `BraceMatchingTest`。

2. 將編輯器分類專案範本加入至專案。 如需詳細資訊，請參閱 [使用編輯器專案範本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3. 刪除現有類別檔案。

## <a name="implement-a-brace-matching-tagger"></a>執行括弧對稱標記
 若要取得類似于 Visual Studio 中所使用的大括弧醒目提示效果，您可以執行類型的標記 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> 。 下列程式碼示範如何在任何嵌套層級上定義大括弧配對的標記。 在此範例中，[] 和的大括弧組會定義在標記函式中 {} ，但在完整語言的執行中，會在語言規格中定義相關的大括弧組。

### <a name="to-implement-a-brace-matching-tagger"></a>若要執行括弧對稱的成對標記

1. 新增類別檔案，並將它命名為 BraceMatching。

2. 匯入下列命名空間。

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. 定義 `BraceMatchingTagger` 繼承自 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 型別的類別 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> 。

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. 加入文字視圖、來源緩衝區、目前快照集點以及一組大括弧配對的屬性。

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. 在標記的函式中，設定屬性並訂閱 view change 事件 <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> 和 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> 。 在此範例中，為了方便說明，也會在此函式中定義相符的配對。

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. 在 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 執行過程中，宣告 TagsChanged 事件。

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. 事件處理常式會更新屬性的目前插入號位置 `CurrentChar` ，並引發 TagsChanged 事件。

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>當目前的字元是左大括弧，或當前一個字元是右大括弧時，請執行方法來比對大括弧，如 Visual Studio 中所示。 找到相符的時，此方法會具現化兩個標記，一個用於左大括弧，另一個用於右大括弧。

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. 下列私用方法會在任何嵌套層級上尋找相符的括弧。 第一個方法會尋找符合開啟字元的結尾字元：

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. 下列 helper 方法會尋找符合結尾字元的開啟字元：

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>執行括弧對稱的成對標記提供者
 除了執行標記之外，您還必須執行和匯出標記提供者。 在此情況下，提供者的內容類型為 "text"。 因此，大括弧比對將會出現在所有類型的文字檔中，但更完整的執行只會將大括弧比對套用至特定的內容類型。

### <a name="to-implement-a-brace-matching-tagger-provider"></a>若要執行括弧對稱的標記提供者

1. 宣告繼承自的標記提供者 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> 、將它命名為 BraceMatchingTaggerProvider，然後使用 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" 和 of 的來匯出它 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> 。

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. 執行 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> 方法以具現化 BraceMatchingTagger。

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>建立並測試程式碼
 若要測試此程式碼，請建立 BraceMatchingTest 方案，並在實驗實例中執行它。

#### <a name="to-build-and-test-bracematchingtest-solution"></a>若要建立及測試 BraceMatchingTest 方案

1. 建置方案。

2. 當您在偵錯工具中執行此專案時，會啟動 Visual Studio 的第二個實例。

3. 建立文字檔，並輸入包含相符括弧的一些文字。

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. 當您將插入點放在左大括弧之前時，應該反白顯示該括弧和相符的右大括弧。 當您將游標放在右大括弧之後，則應該反白顯示該大括弧和相符的左大括弧。

## <a name="see-also"></a>請參閱
- [逐步解說：將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
