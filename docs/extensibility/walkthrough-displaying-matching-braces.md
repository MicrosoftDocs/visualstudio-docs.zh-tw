---
title: 演練:顯示匹配的大括弧 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 107610733ab9b5c8085b3f987fa999250b453d63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697456"
---
# <a name="walkthrough-display-matching-braces"></a>演練:顯示匹配的大括弧
實現基於語言的功能,例如,通過定義要匹配的大括弧來匹配大括弧,並在 caret 位於其中一個大括弧上時向匹配大括弧添加文本標記標記。 您可以在語言上下文中定義大括弧,定義自己的檔名副檔名和內容類型,並將標記僅應用於該類型,或將標記應用於現有內容類型(如"文本")。 以下演練演示如何將大括弧匹配標記應用於「文本」內容類型。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-managed-extensibility-framework-mef-project"></a>建立系統延伸架構 (MEF) 專案

#### <a name="to-create-a-mef-project"></a>建立 MEF 專案

1. 建立編輯器分類器專案。 將方案命名為 `BraceMatchingTest`。

2. 加入專案加入編輯器分類器項範本。 關於詳細資訊,請參考[使用編輯器項目樣本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3. 刪除現有類別檔案。

## <a name="implement-a-brace-matching-tagger"></a>實作大括弧比標記器
 要獲得類似於 Visual Studio 中使用的大括弧突出顯示效果,<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>可以實現類型 標記。 以下代碼演示如何在任何嵌套級別為大括弧對定義標記。 在此示例中,*的大括弧對在{}標記器構造函數中定義,但在完整語言實現中,將在語言規範中定義相關的大括弧對。

### <a name="to-implement-a-brace-matching-tagger"></a>實作大括弧比標記器

1. 添加類檔並將其命名為 Brace 匹配。

2. 匯入以下命名空間。

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. 定義從`BraceMatchingTagger`<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601><xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>類型 繼承的類。

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. 添加文本視圖、源緩衝區、當前快照點以及一組大括弧對的屬性。

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. 在標記器建構函數中,設定屬性並訂閱檢視變更事件<xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged>和<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>。 在此示例中,為了便於說明,匹配對也在構造函數中定義。

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. 作為實現的一<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>部分,聲明 Tag 已更改事件。

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. 事件處理程式更新`CurrentChar`屬性的當前位置並引發 Tag 已更改事件。

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. 實現<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>方法以匹配大括弧,當當前字元是開放大括弧或當前一個字元是緊密大括弧時,如 Visual Studio 中那樣。 找到匹配項時,此方法會實例化兩個標記,一個用於開放大括弧,一個用於緊密大括弧。

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. 以下私有方法在任何嵌套級別查找匹配的大括弧。 第一種方法尋找與開啟字元符合的緊密字元:

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. 以下說明程式方法尋找與近字元符合的開放字元:

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>實現大括弧比標記提供者
 除了實現標記器外,還必須實現並匯出標記提供程式。 在這種情況下,提供程式的內容類型是"文本"。 因此,大括弧匹配將顯示在所有類型的文本檔中,但更全面的實現僅將大括弧匹配應用於特定內容類型。

### <a name="to-implement-a-brace-matching-tagger-provider"></a>實現大括弧比標記提供者

1. 顯示從<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>繼承的標記提供者 ,將檔案為 Brace 符合 Tagger 提供<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>者,然後將其匯<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute><xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>出為文字與 。

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. 實現實例<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>化支架匹配標記的方法。

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>組建及測試代碼
 要測試此代碼,請建構 Brace匹配測試解決方案並在實驗實例中運行它。

#### <a name="to-build-and-test-bracematchingtest-solution"></a>建構和測試大括弧符合測試解決方案

1. 建置方案。

2. 在除錯器中執行此專案時,將啟動 Visual Studio 的第二個實體。

3. 建立文字檔並鍵入一些包含匹配大括弧的文本。

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. 將 care 放置在打開的大括弧之前時,應突出顯示該大括弧和匹配的緊密大括弧。 當您在關閉大括弧之後定位游標時,應突出顯示該大括弧和匹配的打開大括弧。

## <a name="see-also"></a>另請參閱
- [演練:將內容類型連結到檔案名副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
