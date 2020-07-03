---
title: 逐步解說：建立邊界字元 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b94ab61f56d74537758c189adc9c104516f67f92
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905052"
---
# <a name="walkthrough-create-a-margin-glyph"></a>逐步解說：建立邊界字元
您可以使用自訂編輯器延伸模組來自訂編輯器邊界的外觀。 當程式碼批註中出現 "todo" 一字時，本逐步解說會將自訂圖像放在指標邊界上。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選擇性功能。 您稍後也可以安裝 VS SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-mef-project"></a>建立 MEF 專案

1. 建立 c # VSIX 專案。 （在 [**新增專案**] 對話方塊中，選取 [ **Visual c #/** 擴充性]、[ **VSIX 專案**]）。將方案命名為 `TodoGlyphTest` 。

2. 加入編輯器分類器專案專案。 如需詳細資訊，請參閱[使用編輯器專案範本建立擴充](../extensibility/creating-an-extension-with-an-editor-item-template.md)功能。

3. 刪除現有類別檔案。

## <a name="define-the-glyph"></a>定義字型
 藉由執行介面來定義圖像 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> 。

### <a name="to-define-the-glyph"></a>若要定義字型

1. 加入類別檔案，並將它命名為 `TodoGlyphFactory`。

2. 使用宣告來新增下列程式碼。

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. 新增名為 `TodoGlyphFactory` 且會執行的類別 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> 。

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. 新增定義圖像尺寸的私用欄位。

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. 藉 `GenerateGlyph` 由定義圖像使用者介面（UI）元素來執行。 `TodoTag`稍後會在本逐步解說中定義。

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. 新增名為 `TodoGlyphFactoryProvider` 且會執行的類別 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> 。 請使用 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph" 的、在 <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> VsTextMarker 後的、為 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "code" 的，以及 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag 的來匯出此類別。

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. 藉由具現 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> 化來執行方法 `TodoGlyphFactory` 。

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>定義待辦事項標籤和標記
 定義您在先前步驟中定義的 UI 元素與指標邊界之間的關聯性。 建立標籤類型和標記，並使用標記提供者將其匯出。

### <a name="to-define-a-todo-tag-and-tagger"></a>若要定義待辦事項標籤和標記

1. 將新的類別檔案新增至專案，並將其命名為 `TodoTagger` 。

2. 新增下列匯入。

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. 新增名為 `TodoTag`的類別。

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. 修改名為且實作為類型的類別 `TodoTagger` <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> `TodoTag` 。

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. `TodoTagger`針對類別，為 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 和新增要在分類範圍中尋找之文字的私用欄位。

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. 加入設定分類器的函式。

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. 藉 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 由尋找名稱包含 "comment" 一詞且其文字包含搜尋文字的所有分類範圍來執行方法。 每當找到搜尋文字時，就會產生 <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> 類型的新 `TodoTag` 。

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. 宣告 `TagsChanged` 事件。

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. 新增一個名為的類別，它會 `TodoTaggerProvider` <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> 執行，並使用 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" 和 TodoTag 的來匯出它 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> 。

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. 匯入 <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> 。

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. 藉由具現 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> 化來執行方法 `TodoTagger` 。

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>建立並測試程式碼
 若要測試此程式碼，請建立 TodoGlyphTest 方案，並在實驗實例中執行它。

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>若要建立並測試 TodoGlyphTest 解決方案

1. 建置方案。

2. 按**F5**執行專案。 Visual Studio 啟動的第二個實例。

3. 請確定已顯示指示器邊界。 （在 [**工具**] 功能表上，按一下 [**選項**]。 在 [**文字編輯器**] 頁面上，確認已選取 [**指標邊界**]）。

4. 開啟含有批註的程式碼檔案。 將 "todo" 這個字加入其中一個批註區段。

5. 具有深藍色外框的淺藍色圓形會出現在程式碼視窗左邊的指標邊界中。
