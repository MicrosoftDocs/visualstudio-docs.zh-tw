---
title: 演練:顯示快速資訊工具提示 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 47a14ca0692ad0338b56fd1d372307fb0e2ccc4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697443"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>演練:顯示快速資訊工具提示
QuickInfo 是一個 IntelliSense 功能,當使用者在方法名稱上移動指標時,顯示方法簽名和說明。 您可以通過定義要為其提供 QuickInfo 說明的識別碼,然後建立用於顯示內容的工具提示來實現基於語言的功能,例如 QuickInfo。 您可以在語言服務的上下文中定義 QuickInfo,也可以定義自己的檔案名副檔名和內容類型,並僅顯示該類型的 QuickInfo,也可以顯示現有內容類型的 QuickInfo(如"文本")。 這個演練展示如何顯示「文字」內容類型的 QuickInfo。

 本演練中的 QuickInfo 範例顯示當使用者將指標移到方法名稱上時的工具提示。 此設計要求您實現以下四個介面:

- 源介面

- 來源提供者介面

- 控制器介面

- 控制器提供者介面

  來源與控制器提供者是託管延伸框架 (MEF) 元件,負責匯出來源及控制器類別以及匯入服務和代理,如建立工具提示文字緩衝區的<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService><xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>與觸發 QuickInfo 工作階段的 。

  在此範例中,QuickInfo 源使用方法名稱和說明的硬編碼清單,但在完全實現中,語言服務和語言文件負責提供該內容。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您無需從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-mef-project"></a>建立 MEF 專案

### <a name="to-create-a-mef-project"></a>建立 MEF 專案

1. 創建 C# VSIX 專案。 ( 在 **'新增項目'** 對話框中,選擇**視覺化 C# / 可擴充性**,然後選擇**VSIX 專案**。命名解決方案`QuickInfoTest`。

2. 加入專案加入編輯器分類器項範本。 關於詳細資訊,請參考[使用編輯器項目樣本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3. 刪除現有類別檔案。

## <a name="implement-the-quickinfo-source"></a>實現快速資訊來源
 QuickInfo 源負責收集標識符集及其說明,並在遇到其中一個標識符時將內容添加到工具提示文本緩衝區。 在此示例中,標識符及其描述只是添加到源構造函數中。

#### <a name="to-implement-the-quickinfo-source"></a>實現快速資訊來源

1. 加入類別檔案，並將它命名為 `TestQuickInfoSource`。

2. 新增對*Microsoft 的引用.VisualStudio.語言.IntelliSense*。

3. 新增下列匯入。

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4. 宣告以<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>的類別並命名`TestQuickInfoSource`。

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5. 為 QuickInfo 源提供者、文字緩衝區以及一組方法名稱和方法簽名添加欄位。 在此範例中,方法名稱和簽名在建構函數中`TestQuickInfoSource`初始化。

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6. 添加一個建構函數,用於設置 QuickInfo 源提供程式和文字緩衝區,並填充方法名稱集以及方法簽名和說明。

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7. 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> 方法。 在此示例中,如果游標位於行或文本緩衝區的末尾,則該方法查找當前單詞或上一個單詞。 如果單詞是方法名稱之一,則該方法名稱的說明將添加到 QuickInfo 內容中。

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8. 您必須實現 Dispose() 方法,<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>因為<xref:System.IDisposable>:

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>實作 QuickInfo 來源供應商
 QuickInfo 源的提供者主要用於匯出自身作為 MEF 元件部分並實例化 QuickInfo 源。 因為它是 MEF 元件部件,因此可以導入其他 MEF 元件部件。

#### <a name="to-implement-a-quickinfo-source-provider"></a>實現 QuickInfo 來源提供者

1. 聲明名為 的名為`TestQuickInfoSourceProvider`的<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>QuickInfo 源<xref:Microsoft.VisualStudio.Utilities.NameAttribute>提供者,並匯出它與「ToolTip QuickInfo<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>源」,<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>一個前=「預設」和一個「文字」。。

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2. 匯入兩個編輯器服務<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>,<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>並將`TestQuickInfoSourceProvider`作為的屬性。

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3. 可<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>傳回`TestQuickInfoSource`新的 。

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>實現快速資訊控制器
 QuickInfo 控制器確定何時顯示 QuickInfo。 在此範例中,當指標位於對應於其中一個方法名稱的單詞上時,將顯示 QuickInfo。 QuickInfo 控制器實現一個滑鼠懸停事件處理程式,該處理程式觸發 QuickInfo 作業階段。

### <a name="to-implement-a-quickinfo-controller"></a>實現快速資訊控制器

1. 宣告以<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>的類別並命名`TestQuickInfoController`。

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2. 為文字檢視、文字檢視中表示的文本緩衝區、QuickInfo 作業階段和QuickInfo控制器提供程式添加私有欄位。

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3. 添加一個建構函數,用於設置欄位並添加滑鼠懸停事件處理程式。

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4. 添加觸發 QuickInfo 會話的滑鼠懸停事件處理程式。

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5. 實現該方法<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>,以便在控制器從文本檢視分離時刪除滑鼠懸停事件處理程式。

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6. 將<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>該方法<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A>和 該方法作為此示例的空方法實現。

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>實現 QuickInfo 控制器提供者
 QuickInfo 控制器的提供者主要用於匯出自身作為 MEF 元件部分並實例化 QuickInfo 控制器。 因為它是 MEF 元件部件,因此可以導入其他 MEF 元件部件。

### <a name="to-implement-the-quickinfo-controller-provider"></a>實現 QuickInfo 控制器提供者

1. 宣告名為`TestQuickInfoControllerProvider`的類別<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>, 實現 ,並匯<xref:Microsoft.VisualStudio.Utilities.NameAttribute>出它與 "ToolTip QuickInfo 控制器"和<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"文字":

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2. 匯入 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> 作為屬性。

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3. 通過實例<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A>化 QuickInfo 控制器來實現該方法。

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>編譯與測試代碼
 要測試此代碼,請建構 QuickInfoTest 解決方案並在實驗實例中運行它。

### <a name="to-build-and-test-the-quickinfotest-solution"></a>建置和測試 QuickInfoTest 解決方案

1. 建置方案。

2. 在除錯器中執行此專案時,將啟動 Visual Studio 的第二個實體。

3. 建立文字檔並鍵入一些包含"添加"和"減法"字樣的文本。

4. 將指標移到「添加」的一個匹配項上。 應顯示`add`方法的簽名和說明。

## <a name="see-also"></a>另請參閱
- [演練:將內容類型連結到檔案名副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
