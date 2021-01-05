---
title: 逐步解說：建立邊界字型 |Microsoft Docs
description: 瞭解如何使用自訂編輯器延伸模組，透過此逐步解說自訂編輯器邊界的外觀。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d8a2ac481ebf76fc2b34be841cd20d15b97fcfa9
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863089"
---
# <a name="walkthrough-create-a-margin-glyph"></a>逐步解說：建立邊界字元
您可以使用自訂編輯器延伸自訂編輯器邊界的外觀。 本逐步解說會在程式碼批註中出現 "todo" 一字時，將自訂圖像放在指標邊界上。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-mef-project"></a>建立 MEF 專案

1. 建立 c # VSIX 專案。  (在 [ **新增專案** ] 對話方塊中，選取 [ **Visual c #/** 擴充性]，然後選取 [ **VSIX 專案**]。 ) 為方案命名 `TodoGlyphTest` 。

2. 加入編輯器分類程式專案專案。 如需詳細資訊，請參閱 [使用編輯器專案範本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3. 刪除現有類別檔案。

## <a name="define-the-glyph"></a>定義圖像
 藉由執行介面來定義圖像 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> 。

### <a name="to-define-the-glyph"></a>若要定義圖像

1. 加入類別檔案，並將它命名為 `TodoGlyphFactory`。

2. 使用宣告加入下列程式碼。

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. 加入名為 `TodoGlyphFactory` 的類別，該類別會執行 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> 。

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. 加入定義圖像尺寸的私用欄位。

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. 藉 `GenerateGlyph` 由定義圖像使用者介面 (UI) 元素來執行。 `TodoTag` 稍後會在本逐步解說中定義。

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. 加入名為 `TodoGlyphFactoryProvider` 的類別，該類別會執行 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> 。 使用 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph"、 <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> "VsTextMarker"、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "code" 和 of TodoTag 的來匯出這個類別 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> 。

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. 藉由具現 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> 化來執行方法 `TodoGlyphFactory` 。

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>定義 Todo 標記和標記
 定義您在先前步驟中所定義的 UI 元素與指標邊界之間的關聯性。 使用標記提供者建立標記類型和標記，並將它匯出。

### <a name="to-define-a-todo-tag-and-tagger"></a>若要定義 todo 標記和標記

1. 將新的類別檔案加入至專案，並將其命名為 `TodoTagger` 。

2. 新增下列匯入。

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. 新增名為 `TodoTag`的類別。

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. 修改型別為 `TodoTagger` 之 implements 的類別 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> `TodoTag` 。

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. 針對 `TodoTagger` 類別，加入的私用欄位， <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 以及要在分類範圍中尋找的文字。

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. 加入設定分類器的函式。

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. 藉 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 由尋找所有分類範圍，其名稱中包含 "comment" 這個字，而其文字包含搜尋文字，來執行方法。 只要找到搜尋文字，就會傳回型別的新 <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> `TodoTag` 。

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. 宣告 `TagsChanged` 事件。

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. 加入名為的類別， `TodoTaggerProvider` 該類別 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> 會執行，並使用 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "code" 和 of <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag 來匯出。

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

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>若要建立及測試 TodoGlyphTest 方案

1. 建置方案。

2. 按下 **F5** 來執行專案。 Visual Studio 的第二個實例會啟動。

3. 請確定顯示的是指標邊界。  (在 [ **工具** ] 功能表上，按一下 [ **選項**]。 在 [ **文字編輯器** ] 頁面上，確認已選取 [ **指標邊界** ]。 ) 

4. 開啟具有批註的程式碼檔案。 將 "todo" 這個字新增至其中一個批註區段。

5. 具有深藍色外框的淺藍色圓形會出現在程式碼視窗左邊的指標邊界中。
