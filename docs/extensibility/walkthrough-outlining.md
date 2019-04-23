---
title: 逐步解說：大綱 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 908b2f2b7a0dc055065abd96df3eb4495ad30ce8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056077"
---
# <a name="walkthrough-outlining"></a>逐步解說：大綱
設定語言為基礎的功能，例如藉由定義的類型，您想要展開或摺疊的文字區域的大綱。 您可以定義區域中的內容語言服務，或定義您自己的檔案名稱副檔名和內容類型和區定義套用至該類型，或套用至現有的內容類型 （例如 「 文字 」） 的區域定義。 本逐步解說示範如何定義及顯示大綱區域。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從下載中心取得。 它包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-managed-extensibility-framework-mef-project"></a>建立 Managed Extensibility Framework (MEF) 專案

### <a name="to-create-a-mef-project"></a>建立 MEF 專案

1. 建立 VSIX 專案。 將方案命名為 `OutlineRegionTest`。

2. 將編輯器分類器項目範本加入專案。 如需詳細資訊，請參閱 <<c0> [ 使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3. 刪除現有類別檔案。

## <a name="implement-an-outlining-tagger"></a>實作大綱的標記者
 一種標記標示大綱區域 (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>)。 此標記會提供標準大綱行為。 可以展開或摺疊的外框的區域。 標示外框的區域將以加號 (**+**) 如果已摺疊或減號 (**-**) 如果已展開，並展開的區域由一條垂直線 demarcated。

 下列步驟示範如何定義會建立以括弧分隔的所有區域的大綱區域的標記者 (**[**，**]**)。

### <a name="to-implement-an-outlining-tagger"></a>若要實作大綱的標記者

1. 加入類別檔案，並將它命名為 `OutliningTagger`。

2. 匯入下列命名空間。

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. 建立一個名為`OutliningTagger`，並讓它實作<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. 新增一些欄位來追蹤文字緩衝區和快照集，並累積應該標記為大綱區域的線路組。 此程式碼包含一份代表大綱區域的區域物件 （若要稍後定義）。

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. 新增標記者建構函式初始化欄位，剖析緩衝區，並新增事件處理常式，以<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>事件。

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. 實作<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>方法，它會具現化標記延伸。 這個範例假設在跨<xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection>中傳遞至方法是連續的雖然它不一定如此。 這個方法中，具現化新的標記範圍的每個大綱區域。

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. 宣告`TagsChanged`事件處理常式。

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. 新增`BufferChanged`回應的事件處理常式<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>藉由剖析文字緩衝的事件。

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. 新增方法以剖析緩衝區。 此處提供的範例是僅供說明。 以同步方式將緩衝區剖析成巢狀的大綱區域。

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. 下列 helper 方法會取得 1 是最左邊的大括號配對表示的大綱層級的整數。

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. 下列 helper 方法會轉譯 SnapshotSpan （本文稍後的定義） 的區域。

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. 下列程式碼是僅供說明。 它會定義 PartialRegion 類別，其中包含行號和位移開始的大綱區域，以及父區域 （如果有的話） 的參考。 此程式碼可讓剖析器來設定巢狀大綱區域。 衍生的 Region 類別包含結尾的大綱區域的行號的參考。

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>實作標記者提供者
 匯出您的標記的標記者提供者。 標記者提供者會建立`OutliningTagger`的"text"的內容類型或其他傳回緩衝區`OutliningTagger`如果緩衝區已經有一個。

### <a name="to-implement-a-tagger-provider"></a>若要實作的標記者提供者

1. 建立一個名為`OutliningTaggerProvider`實作<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>，並將它匯出的 ContentType 和 TagType 屬性使用。

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. 實作<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>方法，藉由新增`OutliningTagger`緩衝區的屬性。

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>建置和測試程式碼
 若要測試此程式碼，建置 OutlineRegionTest 方案，並在實驗執行個體中執行它。

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>若要建置和測試 OutlineRegionTest 方案

1. 建置方案。

2. 當您執行此專案的偵錯工具時，會啟動 Visual Studio 的第二個執行個體。

3. 建立文字檔 輸入一些文字，其中包含左括號和右括號。

    ```
    [
       Hello
    ]
    ```

4. 應該包含這兩個方括號的大綱區域。 您應該能夠按一下減號左邊的左括號來摺疊大綱區域。 當區域已摺疊，省略符號 (*...*) 應該已摺疊的區域，並包含文字的快顯視窗的左邊會出現**暫留文字**當您移動滑鼠指標的省略符號時，應該會出現。

## <a name="see-also"></a>另請參閱
- [逐步解說：將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)