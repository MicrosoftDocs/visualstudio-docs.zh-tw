---
title: 逐步解說：顯示 QuickInfo 工具提示 |Microsoft Docs
description: 瞭解如何使用本逐步解說來顯示文字內容的 QuickInfo。 QuickInfo 會顯示方法簽章和方法名稱的描述。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: acda716c72d10f35bf8c89978956f62a6d3754dc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078600"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>逐步解說：顯示 QuickInfo 工具提示
QuickInfo 是一項 IntelliSense 功能，會在使用者將指標移至方法名稱上方時，顯示方法簽章和描述。 您可以藉由定義要提供 QuickInfo 描述的識別碼，然後建立要顯示內容的工具提示，來執行以語言為基礎的功能（例如 QuickInfo）。 您可以在語言服務的內容中定義 QuickInfo，或者您可以定義自己的副檔名和內容類型，並只顯示該類型的 QuickInfo，也可以顯示現有內容 (類型的 QuickInfo，例如 "text" ) 。 本逐步解說示範如何顯示「文字」內容類型的 QuickInfo。

 本逐步解說中的 QuickInfo 範例會在使用者將指標移至方法名稱上方時顯示工具提示。 此設計需要您執行下列四個介面：

- 來源介面

- 來源提供者介面

- 控制器介面

- 控制器提供者介面

  來源和控制器提供者 Managed Extensibility Framework (MEF) 元件部分，並負責匯出來源和控制器類別，以及匯入服務和訊息代理程式（例如 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> ），以建立工具提示文字緩衝區，以及會 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> 觸發 QuickInfo 會話的。

  在此範例中，QuickInfo 來源會使用硬式編碼的方法名稱和描述清單，但在完整的執行中，語言服務和語言檔會負責提供該內容。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不需要從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-mef-project"></a>建立 MEF 專案

### <a name="to-create-a-mef-project"></a>建立 MEF 專案

1. 建立 c # VSIX 專案。  (在 [ **新增專案** ] 對話方塊中，選取 [ **Visual c #/** 擴充性]，然後選取 [ **VSIX 專案**]。 ) 為方案命名 `QuickInfoTest` 。

2. 將編輯器分類專案範本加入至專案。 如需詳細資訊，請參閱 [使用編輯器專案範本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3. 刪除現有類別檔案。

## <a name="implement-the-quickinfo-source"></a>執行 QuickInfo 來源
 QuickInfo 來源負責收集一組識別碼及其描述，並在遇到其中一個識別碼時，將內容新增至工具提示文字緩衝區。 在此範例中，只會在來源的函式中新增識別碼及其描述。

#### <a name="to-implement-the-quickinfo-source"></a>若要執行 QuickInfo 來源

1. 加入類別檔案，並將它命名為 `TestQuickInfoSource`。

2. 將參考新增至 *VisualStudio*。

3. 新增下列匯入。

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4. 宣告可執行檔類別 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> ，並為其命名 `TestQuickInfoSource` 。

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5. 加入 QuickInfo 來源提供者的欄位、文字緩衝區，以及一組方法名稱和方法簽章。 在此範例中，方法名稱和簽章會在函式中初始化 `TestQuickInfoSource` 。

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6. 加入可設定 QuickInfo 來源提供者和文字緩衝區的函式，並填入方法名稱的集合，以及方法簽章和描述。

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7. 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> 方法。 在此範例中，方法會尋找目前的單字，或如果游標位於行尾或文字緩衝區的結尾，則為前一個單字。 如果單字是其中一個方法名稱，則會將該方法名稱的描述加入至 QuickInfo 內容。

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8. 您也必須執行 Dispose () 方法，因為它 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> 會 <xref:System.IDisposable> 執行：

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>執行 QuickInfo 來源提供者
 QuickInfo 來源的提供者主要是將本身匯出為 MEF 元件元件，並將 QuickInfo 來源具現化。 因為它是 MEF 元件元件，所以可以匯入其他 MEF 元件部分。

#### <a name="to-implement-a-quickinfo-source-provider"></a>若要執行 QuickInfo 來源提供者

1. 宣告名為的 QuickInfo 來源提供者 `TestQuickInfoSourceProvider` <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider> ，並使用 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip QuickInfo Source"、 <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Before = "default" 和 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" 的來匯出它。

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2. 匯入兩個編輯器服務， <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> 以及 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> 做為的屬性 `TestQuickInfoSourceProvider` 。

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3. 執行 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> 以傳回新的 `TestQuickInfoSource` 。

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>執行 QuickInfo 控制器
 QuickInfo 控制器會決定何時會顯示 QuickInfo。 在此範例中，當指標在對應到其中一個方法名稱的單字上方時，就會出現 QuickInfo。 QuickInfo 控制器會執行可觸發 QuickInfo 會話的滑鼠停留事件處理常式。

### <a name="to-implement-a-quickinfo-controller"></a>若要執行 QuickInfo 控制器

1. 宣告可執行檔類別 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> ，並為其命名 `TestQuickInfoController` 。

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2. 新增文字視圖的私用欄位、文字視圖中表示的文字緩衝區、QuickInfo 會話，以及 QuickInfo 控制器提供者。

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3. 加入設定欄位的函式，並加入滑鼠停留事件處理常式。

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4. 新增會觸發 QuickInfo 會話的滑鼠停留事件處理常式。

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5. 執行 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> 方法，以便在從文字視圖卸離控制器時，移除滑鼠停留事件處理常式。

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6. 在 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> 此範例中，將方法和 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> 方法實作為空白的方法。

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>執行 QuickInfo 控制器提供者
 QuickInfo 控制器的提供者主要是將本身匯出為 MEF 元件元件，並將 QuickInfo 控制器具現化。 因為它是 MEF 元件元件，所以可以匯入其他 MEF 元件部分。

### <a name="to-implement-the-quickinfo-controller-provider"></a>若要執行 QuickInfo 控制器提供者

1. 宣告名為的類別， `TestQuickInfoControllerProvider` 該類別 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider> 會執行，並使用 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip QuickInfo Controller" 和 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" 的來匯出它：

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2. 匯入 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> 作為屬性。

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3. 藉由具現 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> 化 QuickInfo 控制器來執行方法。

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>建立並測試程式碼
 若要測試此程式碼，請建立 QuickInfoTest 方案，並在實驗實例中執行它。

### <a name="to-build-and-test-the-quickinfotest-solution"></a>若要建立及測試 QuickInfoTest 方案

1. 建置方案。

2. 當您在偵錯工具中執行此專案時，會啟動 Visual Studio 的第二個實例。

3. 建立文字檔，並輸入一些文字，其中包含 "add" 和 "減法" 等字。

4. 將指標移至其中一個出現的 [新增]。 應該會顯示簽章和方法的描述 `add` 。

## <a name="see-also"></a>另請參閱
- [逐步解說：將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
