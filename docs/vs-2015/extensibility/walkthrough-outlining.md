---
title: 逐步解說︰ 大綱 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 897ff6a39716f424c40fa587d905847a0dbb3682
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805264"
---
# <a name="walkthrough-outlining"></a>逐步解說︰大綱
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以實作語言為基礎的功能，例如藉由定義的類型，您想要展開或摺疊的文字區域的大綱。 您可以定義區域中的內容語言服務，或您可以定義您自己的檔案名稱擴充功能和內容類型，並區定義套用至該類型，或您可以將區域定義套用至現有的內容類型 （例如 「 文字 」）。 本逐步解說示範如何定義及顯示大綱區域。  
  
## <a name="prerequisites"></a>必要條件  
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>建立 MEF 專案  
  
1.  建立 VSIX 專案。 將方案命名為 `OutlineRegionTest`。  
  
2.  將編輯器分類器項目範本加入專案。 如需詳細資訊，請參閱 <<c0> [ 使用編輯器項目範本建立擴充](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  刪除現有類別檔案。  
  
## <a name="implementing-an-outlining-tagger"></a>實作大綱的標記者  
 一種標記標示大綱區域 (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>)。 此標記會提供標準大綱行為。 可以展開或摺疊的外框的區域。 如果已展開，並展開的區域由一條垂直線 demarcated 如果已摺疊的加號或減號標示外框的區域。  
  
 下列步驟示範如何定義會建立所分隔的所有區域的大綱區域的標記者"["和"]"。  
  
#### <a name="to-implement-an-outlining-tagger"></a>若要實作大綱的標記者  
  
1.  加入類別檔案，並將它命名為 `OutliningTagger`。  
  
2.  匯入下列命名空間。  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#1)]
     [!code-vb[VSSDKOutlineRegionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#1)]  
  
3.  建立一個名為`OutliningTagger`，並讓它實作<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#2)]
     [!code-vb[VSSDKOutlineRegionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#2)]  
  
4.  新增一些欄位來追蹤文字緩衝區和快照集，並累積應該標記為大綱區域的線路組。 此程式碼包含一份代表大綱區域的區域物件 （若要稍後定義）。  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#3)]
     [!code-vb[VSSDKOutlineRegionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#3)]  
  
5.  新增標記者建構函式初始化欄位，剖析緩衝區，並新增事件處理常式，以<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>事件。  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#4)]
     [!code-vb[VSSDKOutlineRegionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#4)]  
  
6.  實作<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>方法，它會具現化標記延伸。 這個範例假設在跨<xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection>中傳遞至方法是連續的雖然這不一定如此。 這個方法中，具現化新的標記範圍的每個大綱區域。  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#5)]
     [!code-vb[VSSDKOutlineRegionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#5)]  
  
7.  宣告`TagsChanged`事件處理常式。  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#6)]
     [!code-vb[VSSDKOutlineRegionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#6)]  
  
8.  新增`BufferChanged`回應的事件處理常式<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>藉由剖析文字緩衝的事件。  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#7)]
     [!code-vb[VSSDKOutlineRegionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#7)]  
  
9. 新增方法以剖析緩衝區。 此處提供的範例是僅供說明。 以同步方式將緩衝區剖析成巢狀的大綱區域。  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#8)]
     [!code-vb[VSSDKOutlineRegionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#8)]  
  
10. 下列 helper 方法會取得 1 是最左邊的大括號配對表示的大綱層級的整數。  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#9)]
     [!code-vb[VSSDKOutlineRegionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#9)]  
  
11. 下列 helper 方法會轉譯 SnapshotSpan （稍後在本主題中定義） 的區域。  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#10)]
     [!code-vb[VSSDKOutlineRegionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#10)]  
  
12. 下列程式碼是僅供說明。 它會定義 PartialRegion 類別，其中包含行號和位移開始的大綱區域，以及父區域 （如果有的話） 的參考。 這可讓剖析器來設定巢狀大綱區域。 衍生的 Region 類別包含結尾的大綱區域的行號的參考。  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#11)]
     [!code-vb[VSSDKOutlineRegionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#11)]  
  
## <a name="implementing-a-tagger-provider"></a>實作標記者提供者  
 您必須針對您的標記者來匯出標記者提供者。 標記者提供者會建立`OutliningTagger`的"text"的內容類型或其他傳回緩衝區`OutliningTagger`如果緩衝區已經有一個。  
  
#### <a name="to-implement-a-tagger-provider"></a>若要實作的標記者提供者  
  
1.  建立一個名為`OutliningTaggerProvider`實作<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>，並將它匯出的 ContentType 和 TagType 屬性使用。  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#12)]
     [!code-vb[VSSDKOutlineRegionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#12)]  
  
2.  實作<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>方法，藉由新增`OutliningTagger`緩衝區的屬性。  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#13)]
     [!code-vb[VSSDKOutlineRegionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#13)]  
  
## <a name="building-and-testing-the-code"></a>建置和測試程式碼  
 若要測試此程式碼，建置 OutlineRegionTest 方案，並在實驗執行個體中執行它。  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>若要建置和測試 OutlineRegionTest 方案  
  
1.  建置方案。  
  
2.  當您在偵錯工具中執行這個專案時，會具現化第二個 Visual Studio 執行個體。  
  
3.  建立文字檔 輸入一些文字，其中包含左括號和右大括號。  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  應該包含這兩個大括號的大綱區域。 您應該能夠按一下減號左邊的左大括號來摺疊大綱區域。 當區域已摺疊，省略符號 （...） 應該已摺疊的區域，並包含文字的快顯視窗的左邊會出現**暫留文字**當您移動滑鼠指標的省略符號時，應該會出現。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說︰將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

