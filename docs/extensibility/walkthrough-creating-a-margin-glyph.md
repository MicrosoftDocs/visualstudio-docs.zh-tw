---
title: 逐步解說：建立邊界字型 |Microsoft Docs
description: 瞭解如何使用自訂編輯器延伸模組，透過此逐步解說自訂編輯器邊界的外觀。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec5eecef40220c2cf2d4e3f1ece8eb5eb763bdeb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217407"
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

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet1":::

3. 加入名為 `TodoGlyphFactory` 的類別，該類別會執行 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> 。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet2":::

4. 加入定義圖像尺寸的私用欄位。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet3":::

5. 藉 `GenerateGlyph` 由定義圖像使用者介面 (UI) 元素來執行。 `TodoTag` 稍後會在本逐步解說中定義。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet4":::

6. 加入名為 `TodoGlyphFactoryProvider` 的類別，該類別會執行 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> 。 使用 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph"、 <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> "VsTextMarker"、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "code" 和 of TodoTag 的來匯出這個類別 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> 。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet5":::

7. 藉由具現 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> 化來執行方法 `TodoGlyphFactory` 。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet6":::

## <a name="define-a-todo-tag-and-tagger"></a>定義 Todo 標記和標記
 定義您在先前步驟中所定義的 UI 元素與指標邊界之間的關聯性。 使用標記提供者建立標記類型和標記，並將它匯出。

### <a name="to-define-a-todo-tag-and-tagger"></a>若要定義 todo 標記和標記

1. 將新的類別檔案加入至專案，並將其命名為 `TodoTagger` 。

2. 新增下列匯入。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet7":::

3. 新增名為 `TodoTag`的類別。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet8":::

4. 修改型別為 `TodoTagger` 之 implements 的類別 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> `TodoTag` 。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet9":::

5. 針對 `TodoTagger` 類別，加入的私用欄位， <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 以及要在分類範圍中尋找的文字。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet10":::

6. 加入設定分類器的函式。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet11":::

7. 藉 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 由尋找所有分類範圍，其名稱中包含 "comment" 這個字，而其文字包含搜尋文字，來執行方法。 只要找到搜尋文字，就會傳回型別的新 <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> `TodoTag` 。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet12":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet12":::

8. 宣告 `TagsChanged` 事件。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet13":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet13":::

9. 加入名為的類別， `TodoTaggerProvider` 該類別 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> 會執行，並使用 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "code" 和 of <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag 來匯出。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet14":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet14":::

10. 匯入 <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> 。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet15":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet15":::

11. 藉由具現 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> 化來執行方法 `TodoTagger` 。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet16":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet16":::

## <a name="build-and-test-the-code"></a>建立並測試程式碼
 若要測試此程式碼，請建立 TodoGlyphTest 方案，並在實驗實例中執行它。

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>若要建立及測試 TodoGlyphTest 方案

1. 建置方案。

2. 按下 **F5** 來執行專案。 Visual Studio 的第二個實例會啟動。

3. 請確定顯示的是指標邊界。  (在 [ **工具** ] 功能表上，按一下 [ **選項**]。 在 [ **文字編輯器** ] 頁面上，確認已選取 [ **指標邊界** ]。 ) 

4. 開啟具有批註的程式碼檔案。 將 "todo" 這個字新增至其中一個批註區段。

5. 具有深藍色外框的淺藍色圓形會出現在程式碼視窗左邊的指標邊界中。
