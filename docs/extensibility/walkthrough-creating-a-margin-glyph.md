---
title: 逐步解說：建立邊界圖像 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 745e54856f1859857877eab18c18b2ee9eb62ead
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56721933"
---
# <a name="walkthrough-create-a-margin-glyph"></a>逐步解說：建立邊界字符
您可以使用自訂編輯器擴充功能，來自訂編輯器邊界的外觀。 本逐步解說會將自訂圖像 （glyph） 放在指示區邊界中，每當"todo"這個字出現在程式碼註解。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從下載中心取得。 它包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-mef-project"></a>建立 MEF 專案

1.  建立 C# VSIX 專案。 (在**新的專案**對話方塊中，選取**Visual C# / 擴充性**，然後**VSIX 專案**。)將方案命名為 `TodoGlyphTest`。

2.  新增編輯器的分類器專案項目。 如需詳細資訊，請參閱 <<c0> [ 使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3.  刪除現有類別檔案。

## <a name="define-the-glyph"></a>定義圖像 （glyph）
 定義圖像 （glyph） 執行<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>介面。

### <a name="to-define-the-glyph"></a>若要定義圖像 （glyph）

1.  加入類別檔案，並將它命名為 `TodoGlyphFactory`。

2.  使用宣告，新增下列程式碼。

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3.  新增名為類別`TodoGlyphFactory`實作<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>。

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4.  加入私用欄位來定義維度的圖像 （glyph）。

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5.  實作`GenerateGlyph`藉由定義圖像 （glyph） 使用者介面 (UI) 項目。 `TodoTag` 在此逐步解說稍後定義。

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6.  新增名為類別`TodoGlyphFactoryProvider`實作<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>。 匯出此類別<xref:Microsoft.VisualStudio.Utilities.NameAttribute>的 「 TodoGlyph"，<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>的後 VsTextMarker<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>的 「 程式碼 」 和<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>TodoTag。

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7.  實作<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A>方法以具現化`TodoGlyphFactory`。

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>定義的待辦事項標記和標記者
 定義上一個步驟中所定義的 UI 元素，並指示區邊界之間的關聯性。 建立標記類型和標記，並使用標記者提供者就可以將它匯出它。

### <a name="to-define-a-todo-tag-and-tagger"></a>若要定義的待辦事項標記和標記者

1.  將新的類別檔案加入至專案並將它命名`TodoTagger`。

2.  新增下列匯入。

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3.  新增類別，名為`TodoTag`。

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4.  修改名為的類別`TodoTagger`可實<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>型別的`TodoTag`。

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5.  若要`TodoTagger`類別，新增私用欄位<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>和文字，以在分類中找到跨越。

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6.  新增設定的分類器的建構函式。

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7.  實作<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>找出所有分類的方法涵蓋其名稱包含"註解 」，以及其文字包含搜尋文字。 每當找到搜尋文字，則傳回產生的新<xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>型別的`TodoTag`。

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8.  宣告`TagsChanged`事件。

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. 新增名為類別`TodoTaggerProvider`可實<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>，並將它與匯出<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>的 「 程式碼 」 和<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>TodoTag。

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. 匯入<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>。

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. 實作<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>方法以具現化`TodoTagger`。

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>建置和測試程式碼
 若要測試此程式碼，建置 TodoGlyphTest 方案，並在實驗執行個體中執行它。

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>若要建置和測試 TodoGlyphTest 方案

1.  建置方案。

2.  執行專案，藉由按下**F5**。 啟動 Visual Studio 的第二個執行個體。

3.  請確定會顯示 指示區邊界。 (在**工具**功能表上，按一下**選項**。 在**文字編輯器**頁面上，請確定**指示區邊界**已選取。)

4.  開啟具有註解的程式碼檔案。 將 word"todo"新增至其中一個註解區段。

5.  具有深藍色外框的淺藍色圓形會出現在左邊的程式碼視窗的指示區邊界。