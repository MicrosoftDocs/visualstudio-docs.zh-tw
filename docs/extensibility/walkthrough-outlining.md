---
title: "逐步解說: 大綱 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，新的大綱"
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 30
---
# 逐步解說: 大綱
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以實作語言為基礎的功能，例如藉由定義您想要展開或摺疊的文字區域的大綱。 您可以定義區域中的內容語言服務，您可以定義您的檔案名稱副檔名和內容類型，並區定義套用至該類型，或您可以將區域定義套用至現有的內容類型 \(例如 「 文字 」\)。 此逐步解說示範如何定義及顯示大綱區域。  
  
## 必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## Managed Extensibility Framework \(MEF\)  
  
#### 建立 MEF 專案  
  
1.  建立 VSIX 專案。 將方案命名為 `OutlineRegionTest`。  
  
2.  將編輯器分類項目範本加入至專案。 如需詳細資訊，請參閱[使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  刪除現有類別檔案。  
  
## 實作大綱標註器  
 一種標記標示大綱區域 \(<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>\)。 此標記會提供標準大綱行為。 可以展開或摺疊的大綱的區域。 外框的區域會標示為如果已摺疊的加號或減號展開，並展開的區域由一條垂直線區分哪些。  
  
 下列步驟示範如何定義建立大綱區域所分隔的所有區域的標註器"\["和"\]"。  
  
#### 若要實作大綱標註器  
  
1.  將類別檔案，並將它 `OutliningTagger`。  
  
2.  匯入下列命名空間。  
  
     [!code-cs[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]  
  
3.  建立一個名為 `OutliningTagger`, ，並將它實作 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-cs[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]  
  
4.  加入一些欄位來追蹤文字緩衝區和快照集，並累積的行應該標記為大綱區域集合。 這個程式碼包含代表大綱區域的區域物件 \(若要稍後定義\) 的清單。  
  
     [!code-cs[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]  
  
5.  加入標註器建構函式初始化欄位，剖析緩衝區，並加入至事件處理常式 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 事件。  
  
     [!code-cs[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]  
  
6.  實作 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 方法，它會具現化該標記延伸。 這個範例假設在範圍 <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> 方法中傳遞是連續的雖然這不一定如此。 這個方法會產生新的標記範圍每個大綱區域。  
  
     [!code-cs[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]  
  
7.  宣告 `TagsChanged` 事件處理常式。  
  
     [!code-cs[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]  
  
8.  新增 `BufferChanged` 回應的事件處理常式 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 剖析文字緩衝區的事件。  
  
     [!code-cs[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]  
  
9. 加入的方法，會剖析緩衝區。 此處提供的範例是僅供說明。 以同步方式將緩衝區剖析成巢狀的大綱區域。  
  
     [!code-cs[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]  
  
10. 下列 helper 方法會取得代表的大綱層級 1 是最左邊的大括號組的整數。  
  
     [!code-cs[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]  
  
11. 下列 helper 方法會轉譯 SnapshotSpan \(本主題稍後的定義\) 的區域。  
  
     [!code-cs[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]  
  
12. 下列程式碼是僅供說明。 它會定義 PartialRegion 類別，其中包含行號和位移開始的大綱區域，以及 \(如果有的話\) 的上層區域的參考。 這可讓剖析器設定巢狀大綱區域。 在衍生的 Region 類別包含的大綱區域結尾的行號的參考。  
  
     [!code-cs[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]  
  
## 實作標註器提供者  
 您必須針對您的標註器匯出標註器提供者。 標註器提供者會建立 `OutliningTagger` 的 「 文字 」 內容類型，或其他的傳回緩衝區 `OutliningTagger` 如果緩衝區已經有一個。  
  
#### 若要實作標註器提供者  
  
1.  建立一個名為 `OutliningTaggerProvider` 實作 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, ，並將它匯出以 ContentType 與 TagType 屬性。  
  
     [!code-cs[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]  
  
2.  實作 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> 方法藉由新增 `OutliningTagger` 緩衝區的內容。  
  
     [!code-cs[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]  
  
## 建置和測試程式碼  
 若要測試這段程式碼，OutlineRegionTest 方案中建置並執行它的實驗執行個體。  
  
#### 若要建置和測試 OutlineRegionTest 方案  
  
1.  建置方案。  
  
2.  當您在偵錯工具中執行這個專案時，會具現化第二個 Visual Studio 執行個體。  
  
3.  建立文字檔 輸入一些文字，其中包含左括號和右括號。  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  應該包含這兩個大括號中的大綱區域。 您可以按一下減號左邊的左大括號來摺疊的大綱區域。 當區域摺疊，請省略符號 \(...\) 應該會出現已摺疊的區域，並包含文字的快顯視窗的左邊 **暫留文字** 應該會出現省略符號上移動指標時。  
  
## 請參閱  
 [逐步解說: 將內容類型連結至檔案名稱副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)