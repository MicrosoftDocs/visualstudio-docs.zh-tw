---
title: 逐步解說：顯示 QuickInfo 工具提示 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6939ed93a07ab8a51de4fde6a5b063a586dc26de
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56713265"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>逐步解說：顯示 QuickInfo 工具提示
QuickInfo 是 IntelliSense 功能，可顯示方法簽章，並說明當使用者將指標移方法名稱。 您可以實作語言為基礎的功能，例如 QuickInfo 定義您要提供 QuickInfo 描述的識別碼，然後再建立要顯示的內容中的工具提示。 您可以定義 QuickInfo 中的內容語言服務，或您可以定義您自己的檔案名稱擴充功能和內容類型，並顯示 QuickInfo，只要該類型，或對於現有的內容類型 （例如 「 文字 」），您可以顯示 QuickInfo。 本逐步解說示範如何顯示 QuickInfo"text"的內容類型。

 QuickInfo 範例中的，在此逐步解說會顯示工具提示，當使用者將指標移方法名稱。 這項設計會要求您實作這些四個介面：

- 來源介面

- 來源提供者介面

- 控制器介面

- 控制器提供者介面

  來源和控制站提供者是 Managed Extensibility Framework (MEF) 元件部分，而且會負責將匯出的來源和控制器類別，並匯入服務和訊息代理程式這類<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>，這會建立的工具提示文字緩衝區，而<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>，這會觸發 QuickInfo 工作階段。

  在此範例中，QuickInfo 來源使用硬式編碼清單的方法名稱和描述，但在完整的實作中，語言服務和語言文件，負責提供該內容。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 中，您不需要從下載中心安裝 Visual Studio SDK。 它包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-mef-project"></a>建立 MEF 專案

### <a name="to-create-a-mef-project"></a>建立 MEF 專案

1.  建立 C# VSIX 專案。 (在**新的專案**對話方塊中，選取**Visual C# / 擴充性**，然後**VSIX 專案**。)將方案命名為 `QuickInfoTest`。

2.  將編輯器分類器項目範本加入專案。 如需詳細資訊，請參閱 <<c0> [ 使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3.  刪除現有類別檔案。

## <a name="implement-the-quickinfo-source"></a>實作 QuickInfo 來源
 QuickInfo 來源負責收集一組識別碼和其描述和時遇到的其中一個識別項，將內容新增至工具提示文字緩衝。 在此範例中，識別項和其描述只新增來源建構函式。

#### <a name="to-implement-the-quickinfo-source"></a>若要實作 QuickInfo 來源

1.  加入類別檔案，並將它命名為 `TestQuickInfoSource`。

2.  將參考加入*Microsoft.VisualStudio.Language.IntelliSense*。

3.  新增下列匯入。

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4.  宣告類別可實作<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>，並將它命名`TestQuickInfoSource`。

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5.  將欄位加入 QuickInfo 來源提供者、 文字緩衝區，和一組方法名稱和方法簽章。 在此範例中，方法名稱和簽章會在初始化`TestQuickInfoSource`建構函式。

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6.  新增的建構函式設定 QuickInfo 來源提供者和文字緩衝區，並填入一組方法名稱和方法簽章和描述。

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7.  實作 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> 方法。 在此範例中，此方法會尋找目前的字組或前一個字如果資料指標位於線條或文字緩衝區的結尾。 如果單字是其中一個方法名稱，該方法名稱的描述會新增至 QuickInfo 內容。

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8.  您必須也實作 dispose （） 方法，因為<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>實作<xref:System.IDisposable>:

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>實作 QuickInfo 來源提供者
 QuickInfo 來源提供者做主要是為了匯出本身為 MEF 元件組件，並具現化 QuickInfo 來源。 因為它是 MEF 元件組件時，它可以匯入其他 MEF 元件組件。

#### <a name="to-implement-a-quickinfo-source-provider"></a>若要實作 QuickInfo 來源提供者

1.  宣告名為 QuickInfo 來源提供者`TestQuickInfoSourceProvider`可實<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>，並將它與匯出<xref:Microsoft.VisualStudio.Utilities.NameAttribute>的 「 工具提示 QuickInfo 來源 」<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>的 Before ="default"，和<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>為"text"。

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2.  匯入兩個編輯器服務，<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>並<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>，為屬性的`TestQuickInfoSourceProvider`。

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>返回新`TestQuickInfoSource`。

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>實作 QuickInfo 控制器
 QuickInfo 控制站會決定顯示 QuickInfo 時。 在此範例中，透過對應至其中一個方法名稱的文字指標時，會顯示 QuickInfo。 QuickInfo 控制器實作觸發程序 QuickInfo 工作階段的滑鼠停留事件處理常式。

### <a name="to-implement-a-quickinfo-controller"></a>若要實作 QuickInfo 控制器

1.  宣告類別可實作<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>，並將它命名`TestQuickInfoController`。

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2.  加入私用欄位的 [文字] 檢視中，以表示文字檢視、 QuickInfo 工作階段中，並 QuickInfo 控制器提供者的文字緩衝區。

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3.  新增設定的欄位，並將滑鼠暫留時的事件處理常式的建構函式。

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4.  將滑鼠暫留時的事件處理常式觸發 QuickInfo 工作階段。

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>方法，讓文字檢視中卸離控制器時，它會移除滑鼠暫留時的事件處理常式。

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>方法和<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A>做為此範例中的空白方法的方法。

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>實作 QuickInfo 控制器提供者
 QuickInfo 控制器的提供者做主要是為了匯出本身為 MEF 元件組件，並具現化 QuickInfo 控制站。 因為它是 MEF 元件組件時，它可以匯入其他 MEF 元件組件。

### <a name="to-implement-the-quickinfo-controller-provider"></a>若要實作 QuickInfo 控制器提供者

1.  宣告類別，名為`TestQuickInfoControllerProvider`可實<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>，並將它與匯出<xref:Microsoft.VisualStudio.Utilities.NameAttribute>的 「 工具提示 QuickInfo 控制器 」 和<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>為"text":

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2.  匯入 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> 作為屬性。

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A>藉由執行個體化 QuickInfo 控制站的方法。

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>建置和測試程式碼
 若要測試此程式碼，建置 QuickInfoTest 方案，並在實驗執行個體中執行它。

### <a name="to-build-and-test-the-quickinfotest-solution"></a>若要建置和測試 QuickInfoTest 方案

1.  建置方案。

2.  當您執行此專案的偵錯工具時，會啟動 Visual Studio 的第二個執行個體。

3.  建立文字檔案和一些文字，其中包含單字"add"的類型和 「 減去 」。

4.  將指標移到其中的項目之 [新增]。 簽章與描述`add`方法應該會顯示。

## <a name="see-also"></a>另請參閱
- [逐步解說：將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)