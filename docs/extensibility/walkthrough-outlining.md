---
title: 演練:大綱 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97b9dcbb2a24f1a3ed336a4a6bb7de4a15e907b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697218"
---
# <a name="walkthrough-outlining"></a>逐步解說︰大綱
設置基於語言的功能,例如通過定義要展開或摺疊的文本區域類型來大綱排列。 您可以在語言服務上下文中定義區域,或者定義自己的檔名副檔名和內容類型,並將區域定義僅應用於該類型,或者將區域定義應用於現有內容類型(如"文本")。 本演練演示如何定義和顯示大綱區域。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-managed-extensibility-framework-mef-project"></a>建立系統延伸架構 (MEF) 專案

### <a name="to-create-a-mef-project"></a>建立 MEF 專案

1. 建立 VSIX 專案。 將方案命名為 `OutlineRegionTest`。

2. 加入專案加入編輯器分類器項範本。 關於詳細資訊,請參考[使用編輯器項目樣本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3. 刪除現有類別檔案。

## <a name="implement-an-outlining-tagger"></a>實現大綱標記器
 大綱區域用一種標記 (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>) 標記。 此標記提供標準大綱行為。 可以展開或摺疊概述的區域。 如果已摺疊,則輪廓區域**+**()或"減號"()()()**-** 表示,並且擴展區域由垂直線劃定。

 以下步驟演示如何定義標記器,該標記器為由括弧 **(*****)** 分隔的所有區域創建大綱區域。

### <a name="to-implement-an-outlining-tagger"></a>實現大綱標記

1. 加入類別檔案，並將它命名為 `OutliningTagger`。

2. 匯入以下命名空間。

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. 建立名為的`OutliningTagger`類別,並讓它實<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>作 :

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. 添加一些欄位以跟蹤文本緩衝區和快照,並累積應標記為大綱區域的行集。 此代碼包括表示大綱區域的區域物件清單(稍後定義)。

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. 添加標記器建構函數,該建構函數將初始化欄位、分析緩衝區並將事件處理程式添加到<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>事件。

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. 實現該方法<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>,該方法實例化標記範圍。 此示例假定<xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection>傳入到方法的跨度是連續的,儘管可能並不總是這樣。 此方法實例化每個大綱區域的新標記範圍。

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. 聲明事件`TagsChanged`處理程式。

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. 通過分析`BufferChanged`文本緩衝區添加<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>回應 事件的事件處理程式。

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. 添加分析緩衝區的方法。 此處給出的示例僅用於說明。 它將緩衝區同步解析為嵌套大綱區域。

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. 以下説明器方法獲取表示大綱級別的整數,以便 1 是最左側的大括弧對。

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. 以下説明器方法將區域(本文後面定義)轉換為快照範圍。

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. 以下代碼僅用於說明。 它定義一個部分區域類,其中包含大綱區域開頭的行號和偏移量,以及對父區域(如果有)的引用。 此代碼使解析器能夠設置嵌套的大綱區域。 派生的「區域」類包含對大綱區域末尾的行號的引用。

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>提供標記提供者
 匯出標記器的標記提供程式。 標記提供者為「文字」`OutliningTagger`內容類型的緩衝區建立一個緩衝區,或者如果緩衝區已有緩衝區`OutliningTagger`, 則傳回 。

### <a name="to-implement-a-tagger-provider"></a>提供標記提供者

1. 創建一個名為`OutliningTaggerProvider`<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>的 類,實現 ,並匯出它與 ContentType 和 TagType 屬性。

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. 通過將<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>`OutliningTagger`a 添加到緩衝區的屬性來實現該方法。

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>組建及測試代碼
 要測試此代碼,請生成大綱區域測試解決方案並在實驗實例中運行它。

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>建構及測試大綱區域測試解決方案

1. 建置方案。

2. 在除錯器中執行此專案時,將啟動 Visual Studio 的第二個實體。

3. 建立文字檔 鍵入一些包含左括弧和右括弧的文本。

    ```
    [
       Hello
    ]
    ```

4. 應該有一個包含兩個括弧的大綱區域。 您應該能夠按一下開放括弧左側的減號以折疊大綱區域。 當區域摺疊時,橢圓符號 (*...)* 應出現在摺疊區域的左側,並且當您將指標移到橢圓上時,應會出現包含文本**懸停文本**的彈出視窗。

## <a name="see-also"></a>另請參閱
- [演練:將內容類型連結到檔案名副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
