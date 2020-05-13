---
title: 演練:創建邊距字形 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9588b150dd795fc2bc5e6c55d8f6e2359f609939
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697693"
---
# <a name="walkthrough-create-a-margin-glyph"></a>演練:建立邊距字形
您可以使用自訂編輯器擴展自定義編輯器邊距的外觀。 本演練在代碼註釋中出現單詞"待做"時,在指標邊距上放置自定義字形。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-mef-project"></a>建立 MEF 專案

1. 創建 C# VSIX 專案。 ( 在 **'新增項目'** 對話框中,選擇**視覺化 C# / 可擴充性**,然後選擇**VSIX 專案**。命名解決方案`TodoGlyphTest`。

2. 添加編輯器分類器項目項。 關於詳細資訊,請參考[使用編輯器項目樣本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3. 刪除現有類別檔案。

## <a name="define-the-glyph"></a>定義字形
 通過運行<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>介面定義字形。

### <a name="to-define-the-glyph"></a>定義字形

1. 加入類別檔案，並將它命名為 `TodoGlyphFactory`。

2. 使用聲明添加以下代碼。

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. 新增名為`TodoGlyphFactory`的類別<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>,實現 。

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. 添加定義字形尺寸的私有欄位。

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. 通過`GenerateGlyph`定義字形用戶介面 (UI) 元素來實現。 `TodoTag`在本演練的後面部分定義。

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. 新增名為`TodoGlyphFactoryProvider`的類別<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>,實現 。 匯出此類<xref:Microsoft.VisualStudio.Utilities.NameAttribute>與"TodoGlyph",<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>一 個後VsTextMarker,<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>一個 "代碼",和TodoTag。 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. 通過實例<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A>化`TodoGlyphFactory`實現 方法。

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>定義 Todo 標籤與標記器
 定義在前面的步驟中定義的 UI 元素與指標邊距之間的關係。 創建標記類型並標記,並使用標記提供程式匯出標記。

### <a name="to-define-a-todo-tag-and-tagger"></a>定義 todo 標籤與標記器

1. 新增檔案加入新的類別檔將命名為`TodoTagger`。

2. 新增下列匯入。

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. 新增名為 `TodoTag`的類別。

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. 變更名為`TodoTagger`的類別,<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>該`TodoTag`一個提供者的類型 。

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. 到`TodoTagger`類中,為<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>和添加私有欄位,供在分類範圍內查找的文本。

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. 添加設置分類器的構造函數。

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. 通過查找<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>名稱包括單詞"註釋"且其文本包含搜索文本的所有分類範圍來實現該方法。 您可以找到搜尋文字時,都會傳回<xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>新的`TodoTag`型態 。

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. 宣告事件`TagsChanged`。

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. 添加名為`TodoTaggerProvider`的<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>類, 實現 ,<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>然後匯出它<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>與 "代碼"和 TodoTag。

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. 匯入<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>。

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. 通過實例<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>化`TodoTagger`實現 方法。

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>組建及測試代碼
 要測試此代碼,請建構 TodoGlyphTest 解決方案並在實驗實例中運行它。

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>建構及測試 TodoGlyphTest 解決方案

1. 建置方案。

2. 按**F5**運行專案。 視覺工作室的第二個實例開始。

3. 確保顯示指標邊距。 (在 **"工具"** 選單上,按**下 "選項**"。 在 **「文字編輯器」** 頁上,請確保選擇了**指標邊距**。

4. 打開具有註解的代碼檔。 將單詞"todo"添加到其中一個註釋部分。

5. 代碼視窗左側的指標邊距中將顯示一個深藍色圓,帶有深藍色輪廓。
