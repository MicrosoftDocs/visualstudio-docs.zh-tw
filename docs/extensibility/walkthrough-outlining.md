---
title: 逐步解說：大綱 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb338803d50b2ecc9af8c8db6a6b6dc2f3631161
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85906177"
---
# <a name="walkthrough-outlining"></a>逐步解說︰大綱
藉由定義您想要展開或折迭的文字區欄位型別，設定以語言為基礎的功能，例如大綱。 您可以在語言服務的內容中定義區域，或定義自己的副檔名和內容類型，並只將區域定義套用至該類型，或將區域定義套用至現有的內容類型（例如「文字」）。 本逐步解說示範如何定義和顯示大綱區域。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選擇性功能。 您稍後也可以安裝 VS SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-managed-extensibility-framework-mef-project"></a>建立 Managed Extensibility Framework （MEF）專案

### <a name="to-create-a-mef-project"></a>建立 MEF 專案

1. 建立 VSIX 專案。 將方案命名為 `OutlineRegionTest`。

2. 將編輯器分類器專案範本加入至專案。 如需詳細資訊，請參閱[使用編輯器專案範本建立擴充](../extensibility/creating-an-extension-with-an-editor-item-template.md)功能。

3. 刪除現有類別檔案。

## <a name="implement-an-outlining-tagger"></a>執行大綱標記
 大綱區域會以一種標記（）標示 <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> 。 此標記提供標準大綱行為。 大綱區域可以展開或折迭。 外框的區域會以加號（）標示（如果已折迭 **+** ）或減號（ **-** ）（如果已展開），而展開的區域是由垂直線 config.js 區分。

 下列步驟示範如何定義一個標記，為以方括弧（**[**，**]**）分隔的所有區域建立大綱區域。

### <a name="to-implement-an-outlining-tagger"></a>若要執行大綱標記

1. 加入類別檔案，並將它命名為 `OutliningTagger`。

2. 匯入下列命名空間。

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. 建立名為的類別 `OutliningTagger` ，並讓它執行 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> ：

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. 新增一些欄位來追蹤文字緩衝區和快照集，並累積應標記為大綱區域的線條集合。 這段程式碼包含代表大綱區域的區域物件清單（稍後定義）。

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. 加入會初始化欄位、剖析緩衝區，並將事件處理常式加入至事件的標記函式 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 。

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. 執行 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 方法，以具現化標記範圍。 這個範例假設 <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> 傳入至方法的範圍是連續的，但不一定都是如此。 這個方法會為每個大綱區域具現化新的標記範圍。

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. 宣告 `TagsChanged` 事件處理常式。

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. 藉 `BufferChanged` <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 由剖析文本緩衝區，加入回應事件的事件處理常式。

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. 新增剖析緩衝區的方法。 此處提供的範例僅供說明之用。 它會以同步方式將緩衝區剖析成嵌套大綱區域。

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. 下列 helper 方法會取得一個整數，代表大綱的層級，因此1是最左邊的大括弧配對。

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. 下列 helper 方法會將區域（在本文稍後定義）轉譯為 SnapshotSpan。

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. 下列程式碼僅供說明之用。 它會定義一個 PartialRegion 類別，其中包含大綱區域開頭的行號和位移，以及父區域的參考（如果有的話）。 此程式碼可讓剖析器設定嵌套大綱區域。 衍生的區域類別包含大綱區域結尾行號的參考。

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>執行標記提供者
 匯出標記的標記提供者。 標記提供者會 `OutliningTagger` 為 "text" 內容類型的緩衝區建立， `OutliningTagger` 如果緩衝區已經有一個，則會傳回。

### <a name="to-implement-a-tagger-provider"></a>若要執行標記提供者

1. 建立一個名為的類別，它 `OutliningTaggerProvider` 會執行 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> ，並使用 ContentType 和 TagType 屬性將它匯出。

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>將加入 `OutliningTagger` 至緩衝區的屬性，以執行方法。

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>建立並測試程式碼
 若要測試此程式碼，請建立 OutlineRegionTest 方案，並在實驗實例中執行它。

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>若要建立並測試 OutlineRegionTest 解決方案

1. 建置方案。

2. 當您在偵錯工具中執行此專案時，會啟動 Visual Studio 的第二個實例。

3. 建立文字檔 輸入一些文字，其中包含左括弧和右括弧。

    ```
    [
       Hello
    ]
    ```

4. 應該會有一個包含兩個方括弧的大綱區域。 您應該可以按一下左括弧左邊的減號來折迭大綱區域。 當區域折迭時，省略號符號（*...*）應該會出現在折迭區域的左邊，而當您將指標移至省略號上方時，應該會出現包含文字暫留文字的快**顯**。

## <a name="see-also"></a>另請參閱
- [逐步解說：將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
