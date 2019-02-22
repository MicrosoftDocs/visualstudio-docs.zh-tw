---
title: 逐步解說：顯示簽章說明 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5923efe859f6fe04468e6659d8df46b8b3d2a1cd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981125"
---
# <a name="walkthrough-display-signature-help"></a>逐步解說：顯示簽章說明
簽章說明 (也稱為*參數資訊*) 方法的簽章顯示工具提示中，當使用者輸入的參數清單開始字元 （通常是左括號）。 依照所輸入的參數和參數分隔符號 （通常為逗號），工具提示會更新以顯示下一個參數以粗體顯示。 您可以定義簽章說明中的下列方法： 在語言服務的內容中，定義您自己的副檔名和內容類型，並顯示簽章說明只是該類型，或針對現有的內容類型 (例如，"text") 中顯示 簽章說明。 本逐步解說示範如何以顯示簽章說明 「 文字 」 內容類型。  
  
 簽章說明通常會觸發輸入特定的字元，例如，"("（左括號），以及輸入另一個字元，例如已解除 」) 」 （右括號）。 IntelliSense 功能所觸發的輸入字元可以使用來實作命令處理常式的按鍵輸入 (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面) 和實作的處理常式提供者<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>介面。 若要建立簽章說明來源，也就是加入簽章說明中的簽章的清單，實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>介面和來源提供者執行<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>介面。 提供者是 Managed Extensibility Framework (MEF) 元件組件，而且會負責將匯出的來源和控制器類別及匯入服務和代理程式，比方說， <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>，可以讓您在文字緩衝區中，瀏覽，<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>，此觸發程序的簽章說明工作階段。  
  
 本逐步解說示範如何設定簽章說明，硬式編碼的識別項集。 在完整的實作中，語言則是負責提供該內容項目。  
  
## <a name="prerequisites"></a>必要條件  
 從 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從下載中心取得。 它包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>建立 MEF 專案  
  
#### <a name="to-create-a-mef-project"></a>建立 MEF 專案  
  
1.  建立 C# VSIX 專案。 (在**新的專案**對話方塊中，選取**Visual C# / 擴充性**，然後**VSIX 專案**。)將方案命名為 `SignatureHelpTest`。  
  
2.  將編輯器分類器項目範本加入專案。 如需詳細資訊，請參閱 <<c0> [ 使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  刪除現有類別檔案。  
  
4.  將下列參考加入專案，並確認**CopyLocal**設定為`false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implement-signature-help-signatures-and-parameters"></a>實作簽章說明的簽章和參數  
 簽章協助來源為基礎實作的簽章<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>，其中每一個包含實作的參數<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>。 在完整的實作中，這項資訊會取自語言文件中，但在此範例中，簽章是硬式編碼。  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>若要實作的簽章說明的簽章和參數  
  
1.  加入類別檔案，並將它命名為 `SignatureHelpSource`。  
  
2.  新增下列匯入。  
  
     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]  
  
3.  新增名為類別`TestParameter`實作<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>。  
  
     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]  
  
4.  新增將所有屬性的建構函式。  
  
     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]  
  
5.  新增的屬性<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>。  
  
     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]  
  
6.  新增名為類別`TestSignature`實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>。  
  
     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]  
  
7.  加入一些私用欄位。  
  
     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]  
  
8.  新增的建構函式設定的欄位，並訂閱<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>事件。  
  
     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]  
  
9. 宣告`CurrentParameterChanged`事件。 當使用者填滿其中一種簽章中的參數時，會引發這個事件。  
  
     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]  
  
10. 實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A>屬性，因此它會引發`CurrentParameterChanged`事件屬性值變更時。  
  
     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]  
  
11. 新增方法以引發`CurrentParameterChanged`事件。  
  
     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]  
  
12. 新增方法，藉由比較中的逗號數目來計算目前參數<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>簽章中的逗號數目。  
  
     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]  
  
13. 新增事件處理常式<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>呼叫的事件`ComputeCurrentParameter()`方法。  
  
     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]  
  
14. 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> 屬性。 此屬性會保留<xref:Microsoft.VisualStudio.Text.ITrackingSpan>對應的簽章套用至緩衝區中的文字範圍。  
  
     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]  
  
15. 實作其他參數。  
  
     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]  
  
## <a name="implement-the-signature-help-source"></a>實作簽章說明來源  
 簽章說明來源是您要為其提供資訊的簽章組。  
  
#### <a name="to-implement-the-signature-help-source"></a>若要實作的簽章說明來源  
  
1.  新增名為類別`TestSignatureHelpSource`實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>。  
  
     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]  
  
2.  加入至文字的緩衝區的參考。  
  
     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]  
  
3.  新增設定文字緩衝區和簽章說明來源提供者的建構函式。  
  
     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]  
  
4.  實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> 方法。 在此範例中，簽章是以硬式編碼，但完整的實作中您會從語言文件取得這項資訊。  
  
     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]  
  
5.  Helper 方法`CreateSignature()`提供僅供說明。  
  
     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]  
  
6.  實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> 方法。 在此範例中，有兩個簽章，每個都有兩個參數。 因此，這個方法不需要。 在更完整的實作中，在其中多個簽章說明來源可供使用，這個方法用來決定最高優先順序簽章說明來源是否可以提供相符的簽章。 如果不行，方法會傳回 null，並提供符合項目要求的下一個最高優先順序的來源。  
  
     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]  
  
7.  實作`Dispose()`方法：  
  
     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]  
  
## <a name="implement-the-signature-help-source-provider"></a>實作的簽章說明來源提供者  
 簽章說明來源提供者是負責匯出 Managed Extensibility Framework (MEF) 元件組件，以及具現化的簽章說明來源。  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>若要實作的簽章說明來源提供者  
  
1.  新增名為的類別`TestSignatureHelpSourceProvider`可實<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>，並將它與匯出<xref:Microsoft.VisualStudio.Utilities.NameAttribute>，則<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>為"text"，和<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>的 Before ="default"。  
  
     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]  
  
2.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A>具現化`TestSignatureHelpSource`。  
  
     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]  
  
## <a name="implement-the-command-handler"></a>實作命令處理常式  
 簽章說明通常會觸發是左括號"（"的字元和已解除的右括號"）"字元。 您可以藉由執行中處理這些按鍵<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>以便觸發時收到開頭的簽章說明工作階段括號字元加上已知的方法名稱，並關閉工作階段，當它收到的右括弧字元。  
  
#### <a name="to-implement-the-command-handler"></a>若要實作的命令處理常式  
  
1.  新增名為類別`TestSignatureHelpCommand`實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]  
  
2.  新增私用欄位<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>配接器 （可讓您將命令處理常式新增至鏈結的命令處理常式）、 [文字] 檢視、 簽章說明中的訊息代理程式和工作階段中， <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>，和 [下一步] <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]  
  
3.  加入建構函式來初始化這些欄位，並將命令篩選器新增至鏈結的命令篩選器。  
  
     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]  
  
4.  實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>方法來觸發命令篩選器時收到左括號的簽章說明工作階段 」 （"字元之後的已知的方法名稱，並關閉工作階段，當它收到右括號"）"的字元工作階段仍在作用中時。 在每個案例中，會轉送命令。  
  
     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]  
  
5.  實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法，讓它一律會將轉送的命令。  
  
     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]  
  
## <a name="implement-the-signature-help-command-provider"></a>實作簽章說明命令提供者  
 您可以藉由實作提供的簽章說明命令<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>建立文字檢視時，具現化的命令處理常式。  
  
### <a name="to-implement-the-signature-help-command-provider"></a>若要實作的簽章說明命令提供者  
  
1.  新增名為類別`TestSignatureHelpController`可實<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>並將它與匯出<xref:Microsoft.VisualStudio.Utilities.NameAttribute>， <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>，和<xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>。  
  
     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]  
  
2.  匯入<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>(用來取得<xref:Microsoft.VisualStudio.Text.Editor.ITextView>，給定<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>物件)，則<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>（用來尋找目前的字組），而<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>（以觸發簽章說明工作階段）。  
  
     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]  
  
3.  實作<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A>方法以具現化`TestSignatureCommandHandler`。  
  
     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]  
  
## <a name="build-and-test-the-code"></a>建置和測試程式碼  
 若要測試此程式碼，建置 SignatureHelpTest 方案，並在實驗執行個體中執行它。  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>若要建置和測試 SignatureHelpTest 方案  
  
1.  建置方案。  
  
2.  當您執行此專案的偵錯工具時，會啟動 Visual Studio 的第二個執行個體。  
  
3.  建立文字檔案和一些文字，其中包含單字"add"的類型加上左括號。  
  
4.  輸入左括號之後，您應該會看到工具提示會顯示一份兩個簽章`add()`方法。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)