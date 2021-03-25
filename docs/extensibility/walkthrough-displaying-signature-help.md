---
title: 逐步解說：顯示簽章說明 |Microsoft Docs
description: 瞭解如何使用本逐步解說來顯示文字內容類型的簽章說明。 簽章說明會在工具提示中顯示方法的簽章。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1a9aedc6324eb1d4a57517a10b80348841fa72df
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078496"
---
# <a name="walkthrough-display-signature-help"></a>逐步解說：顯示簽章說明
簽章說明 (也稱為 *參數資訊*) 當使用者輸入參數清單開始字元 (通常是左括弧) 時，就會在工具提示中顯示方法的簽章。 作為參數和參數分隔符號 (通常會輸入逗點) ，工具提示會更新以顯示下一個參數（以粗體顯示）。 您可以用下列方式定義簽章說明：在語言服務的內容中，定義您自己的副檔名和內容類型，以及只顯示該類型的簽章說明，或針對現有的內容類型顯示簽章說明 (例如 "text" ) 。 本逐步解說會示範如何顯示「文字」內容類型的簽章說明。

 簽章說明通常是藉由輸入特定字元來觸發，例如 " (" (左括弧) ，然後輸入另一個字元來關閉，例如 ") " (右括弧) 。 藉由輸入字元所觸發的 IntelliSense 功能，可以使用命令處理常式來處理 (介面) 的按鍵 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ，以及處理介面的處理常式提供者 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 。 若要建立簽章說明來源（這是參與簽章說明的簽章清單），請執行 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> 介面和執行介面的來源提供者 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> 。 提供者 Managed Extensibility Framework (MEF) 元件部分，並負責匯出來源和控制器類別，以及匯入服務和訊息代理程式，例如，可 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> 讓您在文字緩衝區中流覽，以及觸發簽章說明 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> 會話的。

 本逐步解說會示範如何為一組硬式編碼的識別碼設定簽章說明。 在完整的執行中，語言會負責提供該內容。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="creating-a-mef-project"></a>建立 MEF 專案

#### <a name="to-create-a-mef-project"></a>建立 MEF 專案

1. 建立 c # VSIX 專案。  (在 [ **新增專案** ] 對話方塊中，選取 [ **Visual c #/** 擴充性]，然後選取 [ **VSIX 專案**]。 ) 為方案命名 `SignatureHelpTest` 。

2. 將編輯器分類專案範本加入至專案。 如需詳細資訊，請參閱 [使用編輯器專案範本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3. 刪除現有類別檔案。

4. 將下列參考加入至專案，並確認 **CopyLocal** 設定為 `false` ：

     VisualStudio 編輯器

     Microsoft.VisualStudio.Language.Intellisense

     VisualStudio： Interop

     VisualStudio. 14。0

     VisualStudio. TextManager. Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>執行簽章說明簽章和參數
 簽章說明來源是以執行的簽章為基礎 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> ，其中每一個都包含可執行檔參數 <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> 。 在完整的執行中，這項資訊是從語言檔取得的，但在此範例中，簽章是硬式編碼的。

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>若要執行簽章說明簽名和參數

1. 加入類別檔案，並將它命名為 `SignatureHelpSource`。

2. 新增下列匯入。

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3. 加入名為 `TestParameter` 的類別，該類別會執行 <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> 。

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4. 加入可設定所有屬性的函式。

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5. 加入的屬性 <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> 。

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6. 加入名為 `TestSignature` 的類別，該類別會執行 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> 。

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7. 新增一些私用欄位。

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8. 加入可設定欄位及訂閱事件的函式 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 。

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. 宣告 `CurrentParameterChanged` 事件。 當使用者填入簽章中的其中一個參數時，就會引發此事件。

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. 執行 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> 屬性，以便在 `CurrentParameterChanged` 屬性值變更時引發事件。

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. 加入引發事件的方法 `CurrentParameterChanged` 。

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. 藉由比較中的逗號數目與簽章中的逗號數目，來新增計算目前參數的方法 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> 。

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. 加入呼叫方法之事件的事件處理常式 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> `ComputeCurrentParameter()` 。

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> 屬性。 這個屬性會保留 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 對應到簽章所套用的緩衝區中之文字範圍的。

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. 執行其他參數。

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>執行簽章說明來源
 簽章說明來源是一組您提供資訊的簽章。

#### <a name="to-implement-the-signature-help-source"></a>若要執行簽章說明來源

1. 加入名為 `TestSignatureHelpSource` 的類別，該類別會執行 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> 。

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2. 加入文字緩衝區的參考。

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3. 加入可設定文字緩衝區和簽章說明來源提供者的函式。

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4. 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> 方法。 在此範例中，簽章是硬式編碼的，但在完整的執行中，您可以從語言檔取得這項資訊。

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5. Helper 方法 `CreateSignature()` 僅提供說明。

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6. 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> 方法。 在此範例中，只有兩個簽章，每個都有兩個參數。 因此，不需要這個方法。 在更完整的執行中，有一個以上的簽章說明來源可供使用時，此方法會用來決定最高優先順序的簽章說明來源是否可以提供相符的簽章。 如果無法這樣做，方法會傳回 null，並要求下一個最高優先順序的來源提供相符的結果。

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7. 執行 `Dispose()` 方法：

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>執行簽章協助來源提供者
 簽章說明來源提供者負責匯出 Managed Extensibility Framework (MEF) 元件部分，以及將簽章說明來源具現化。

#### <a name="to-implement-the-signature-help-source-provider"></a>若要執行簽章協助來源提供者

1. 加入名為的類別， `TestSignatureHelpSourceProvider` 該類別 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> 會執行，並使用 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" 的、，以及 <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Before = "default" 的來匯出。

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2. 藉 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> 由具現化來實行 `TestSignatureHelpSource` 。

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>執行命令處理常式
 簽章說明通常是由左括弧 " (" 字元所觸發，並以右括弧 ") " 字元關閉。 您可以藉由執行來處理這些按鍵， <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 使其在收到開頭為已知方法名稱的左括弧字元時觸發簽章說明會話，並在收到右括弧字元時關閉會話。

#### <a name="to-implement-the-command-handler"></a>若要執行命令處理常式

1. 加入名為 `TestSignatureHelpCommand` 的類別，該類別會執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 。

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2. 新增 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 介面卡 (的私用欄位，可讓您將命令處理常式新增至命令處理常式鏈) 、文字視圖、簽章說明訊息代理程式和會話、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> 和下一個 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 。

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3. 新增用來初始化這些欄位的函式，並將命令篩選器新增至命令篩選鏈。

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>當命令篩選器在其中一個已知的方法名稱之後收到左括弧 " (" 字元，並在會話仍在使用中時，于接收右括弧 ") " 字元時，請執行方法來觸發簽章說明會話。 在每個案例中，都會轉送此命令。

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5. 執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法，讓它一律轉寄命令。

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>執行 Signature Help 命令提供者
 您可以藉由在建立文字視圖時，藉由執行來將命令處理常式具現化，以提供 Signature Help 命令 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 。

### <a name="to-implement-the-signature-help-command-provider"></a>若要執行 Signature Help 命令提供者

1. 加入名為的類別，這個類別會 `TestSignatureHelpController` <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 使用、和來進行執行和匯出 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> 。

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2. 匯入 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> 用來取得的 (（ <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 假設 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 物件) ）、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> 用來尋找目前單字) 的 (，以及用來觸發簽章說明 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> 會話 (的) 。

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3. 藉由具現 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> 化來執行方法 `TestSignatureCommandHandler` 。

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>建立並測試程式碼
 若要測試此程式碼，請建立 SignatureHelpTest 方案，並在實驗實例中執行它。

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>若要建立及測試 SignatureHelpTest 方案

1. 建置方案。

2. 當您在偵錯工具中執行此專案時，會啟動 Visual Studio 的第二個實例。

3. 建立文字檔，並輸入一些文字，其中包含 "add" 這個字加上左括弧。

4. 輸入左括弧之後，您應該會看到工具提示，顯示該方法的兩個簽章清單 `add()` 。

## <a name="see-also"></a>另請參閱
- [逐步解說：將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
