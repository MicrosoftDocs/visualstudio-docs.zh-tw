---
title: "逐步解說： 大綱 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f503d9e8b0ef125fdb72ea60a9928f308b900993
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-outlining"></a>逐步解說： 大綱
您可以實作以語言為基礎的功能，例如藉由定義的一種您想要展開或摺疊的文字區域的大綱。 您可以定義區域中的語言服務內容或您可以定義您自己的檔案名稱副檔名和內容類型，並區定義套用至該類型，或者您可以將區域定義套用至現有的內容類型 （例如"text")。 本逐步解說示範如何定義及顯示大綱區域。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>建立 MEF 專案  
  
1.  建立 VSIX 專案。 將方案命名`OutlineRegionTest`。  
  
2.  編輯器分類器項目範本加入專案。 如需詳細資訊，請參閱[編輯器項目範本以建立擴充](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  刪除現有類別檔案。  
  
## <a name="implementing-an-outlining-tagger"></a>實作大綱的標記者  
 由一種標記所標記的大綱區域 (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>)。 此標記會提供標準大綱行為。 可展開或摺疊的大綱的區域。 如果已展開節點，並展開的區域由一條垂直線 demarcated 程式如果已摺疊的加號或減號標示大綱的區域。  
  
 下列步驟顯示如何定義會建立所分隔的所有區域的大綱區域的標記者"["和"]"。  
  
#### <a name="to-implement-an-outlining-tagger"></a>實作大綱的標記者  
  
1.  將類別檔案並將其命名`OutliningTagger`。  
  
2.  匯入下列命名空間。  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]  
  
3.  建立一個名為`OutliningTagger`，並讓它實作<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]  
  
4.  加入一些欄位來追蹤的文字緩衝區和快照集，並累積所應標記為大綱區域的程式行設定。 這個程式碼會包含代表大綱區域的區域物件 （若要稍後即將定義） 的清單。  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]  
  
5.  加入標記者建構函式初始化欄位，剖析緩衝區，並加入至事件處理常式<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>事件。  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]  
  
6.  實作<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>方法，會具現化標記延伸。 這個範例假設在範圍<xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection>傳遞至方法中是連續的雖然這不一定大小寫。 這個方法會產生大綱區域的每個新標記範圍。  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]  
  
7.  宣告`TagsChanged`事件處理常式。  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]  
  
8.  新增`BufferChanged`回應的事件處理常式<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>藉由剖析文字緩衝區的事件。  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]  
  
9. 加入的方法，會剖析緩衝區。 此處提供的範例是僅供說明。 以同步方式將緩衝區剖析成巢狀的大綱區域。  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]  
  
10. 下列 helper 方法會取得代表的大綱層級，因此 1 是最左邊的大括號組的整數。  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]  
  
11. 下列 helper 方法轉譯 SnapshotSpan 為 （本主題稍後的定義） 的區域。  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]  
  
12. 下列程式碼是僅供說明。 它會定義 PartialRegion 類別，其中包含行號和位移開始的大綱區域，以及父區域 （如果有的話） 的參考。 這可讓剖析器設定巢狀大綱區域。 在衍生的區域類別包含結尾的大綱區域的行號的參考。  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]  
  
## <a name="implementing-a-tagger-provider"></a>實作標記者提供者  
 您必須匯出您標記的標記者提供者。 在標記者提供者會建立`OutliningTagger`的 「 文字 」 內容類型或其他傳回緩衝區`OutliningTagger`如果緩衝區已經有一個。  
  
#### <a name="to-implement-a-tagger-provider"></a>若要實作的標記者提供者  
  
1.  建立一個名為`OutliningTaggerProvider`實作<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>，並將它匯出的 ContentType 和 TagType 屬性。  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]  
  
2.  實作<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>方法藉由新增`OutliningTagger`緩衝區的內容。  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]  
  
## <a name="building-and-testing-the-code"></a>建置和測試程式碼  
 若要測試這段程式碼，建置 OutlineRegionTest 方案，並在實驗執行個體中執行。  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>若要建置和測試 OutlineRegionTest 方案  
  
1.  建置方案。  
  
2.  當您在偵錯工具中執行這個專案時，會具現化第二個 Visual Studio 執行個體。  
  
3.  建立文字檔 輸入一些文字，其中包含左括號和右大括號。  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  應該要有包含這兩個大括號中的大綱區域。 您可以按一下減號左邊的左大括號來摺疊的大綱區域。 當區域已摺疊，省略符號 （...） 應該會顯示已摺疊的區域和快顯視窗包含文字的左邊**暫留文字**指標移省略符號時，應該會出現。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說︰將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)