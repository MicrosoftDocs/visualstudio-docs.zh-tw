---
title: "逐步解說： 顯示簽章說明 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7078ee1e125ca11b0707b22b0d824cd0fc2d75b6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-displaying-signature-help"></a>逐步解說： 顯示簽章說明
簽章說明 (也稱為*參數資訊*) 時，顯示在方法簽章工具提示使用者輸入的參數清單開頭字元 （通常是左括號）。 當具有類型的參數和參數分隔符號 （通常是逗號），工具提示會更新以顯示下一個參數以粗體顯示。 您可以定義的語言服務內容中的 「 簽章說明您可以定義您自己的檔案名稱副檔名和內容類型，並顯示只要該類型的簽章說明或現有的內容類型 （例如，「 文字 」） 可以顯示 簽章說明。 本逐步解說示範如何顯示簽章說明 「 文字 」 內容類型。  
  
 簽章說明通常會觸發輸入特定字元，例如，"("（左括號），並解除輸入另一個字元，例如，") 」 （右括號）。 透過命令處理常式的按鍵動作，即可實作所觸發的輸入字元的 IntelliSense 功能 (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面) 和實作的處理常式提供者<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>介面。 若要建立簽章說明來源，這是參與簽章說明的簽章中的清單，實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>介面和實作的來源提供者<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>介面。 提供者是 Managed Extensibility Framework (MEF) 元件組件，而且負責匯出的來源和控制器類別和匯入服務和代理程式，例如， <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>，可以讓您在文字緩衝區中，瀏覽和<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>，此觸發程序簽章說明工作階段。  
  
 本逐步解說示範如何實作簽章說明的硬式編碼的一組識別碼。 在完整實作中，語言為負責提供該內容。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>建立 MEF 專案  
  
#### <a name="to-create-a-mef-project"></a>建立 MEF 專案  
  
1.  建立 C# VSIX 專案。 (在**新專案**對話方塊中，選取**Visual C# / 擴充性**，然後**VSIX 專案**。)將方案命名`SignatureHelpTest`。  
  
2.  編輯器分類器項目範本加入專案。 如需詳細資訊，請參閱[編輯器項目範本以建立擴充](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  刪除現有類別檔案。  
  
4.  將下列參考加入專案，並確認**CopyLocal**設`false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>實作簽章協助簽章和參數  
 簽章協助來源為基礎實作的簽章<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>，每個均包含實作的參數<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>。 在完整的實作，這項資訊會取自語言文件中，但在此範例中，簽章是硬式編碼。  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>若要實作的簽章說明簽章和參數  
  
1.  將類別檔案並將其命名`SignatureHelpSource`。  
  
2.  加入下列 imports。  
  
     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]  
  
3.  將類別命名為`TestParameter`實作<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>。  
  
     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]  
  
4.  新增設定的所有屬性的建構函式。  
  
     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]  
  
5.  新增的屬性<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>。  
  
     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]  
  
6.  將類別命名為`TestSignature`實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>。  
  
     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]  
  
7.  加入一些私用欄位。  
  
     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]  
  
8.  新增的建構函式設定的欄位，並訂閱<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>事件。  
  
     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]  
  
9. 宣告`CurrentParameterChanged`事件。 當使用者填中其中一個簽章中參數時，會引發這個事件。  
  
     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]  
  
10. 實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A>屬性，因此它會引發`CurrentParameterChanged`事件屬性值變更時。  
  
     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]  
  
11. 加入的方法，引發`CurrentParameterChanged`事件。  
  
     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]  
  
12. 加入的方法，藉由比較在逗號數目計算目前參數<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>的簽章中的逗號分隔的數字。  
  
     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]  
  
13. 加入事件處理常式<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>呼叫的事件`ComputeCurrentParameter()`方法。  
  
     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]  
  
14. 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> 屬性。 這個屬性會保留<xref:Microsoft.VisualStudio.Text.ITrackingSpan>對應於要套用簽章的緩衝區中的文字範圍。  
  
     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]  
  
15. 實作其他參數。  
  
     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]  
  
## <a name="implementing-the-signature-help-source"></a>實作簽章說明來源  
 簽章說明來源是您要為其提供資訊的簽章組。  
  
#### <a name="to-implement-the-signature-help-source"></a>若要實作的簽章說明來源  
  
1.  將類別命名為`TestSignatureHelpSource`實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>。  
  
     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]  
  
2.  加入文字緩衝區的參考。  
  
     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]  
  
3.  新增設定文字緩衝區和簽章說明來源提供者的建構函式。  
  
     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]  
  
4.  實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> 方法。 在此範例中，簽章是硬式編碼，但完整的實作中您會從語言文件取得此資訊。  
  
     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]  
  
5.  Helper 方法`CreateSignature()`提供只供說明。  
  
     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]  
  
6.  實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> 方法。 在此範例中，有兩個簽章，每一個都有兩個參數。 因此，這個方法不需要。 在更完整的實作中，在其中多個簽章說明來源可供使用，這個方法用來決定最高優先權簽章說明來源是否可以提供相符的簽章。 如果不行，方法會傳回 null，並提供符合要求的下一個最高優先順序的來源。  
  
     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]  
  
7.  實作 dispose （） 方法：  
  
     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>實作簽章說明來源提供者  
 簽章說明來源提供者是負責匯出 Managed Extensibility Framework (MEF) 元件組件，以及具現化的簽章說明來源。  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>若要實作的簽章說明來源提供者  
  
1.  將類別命名為`TestSignatureHelpSourceProvider`實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>，並將它與匯出<xref:Microsoft.VisualStudio.Utilities.NameAttribute>、<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>的 「 文字 」，和<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>的 Before ="default"。  
  
     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]  
  
2.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A>藉由執行個體化`TestSignatureHelpSource`。  
  
     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]  
  
## <a name="implementing-the-command-handler"></a>實作的命令處理常式  
 簽章說明通常會觸發 (字元和已解除的) 字元。 您可以藉由實作來處理這些按鍵<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>以便觸發當它收到的簽章說明工作階段 (字元前面有已知的方法名稱，並關閉工作階段，當它收到) 字元。  
  
#### <a name="to-implement-the-command-handler"></a>若要實作的命令處理常式  
  
1.  將類別命名為`TestSignatureHelpCommand`實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]  
  
2.  加入私用欄位的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>介面卡 （它可讓您將命令處理常式新增至鏈結的命令處理常式）、 文字檢視、 簽章說明 broker 和工作階段， <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>，下一個<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]  
  
3.  新增的建構函式來初始化這些欄位，並將命令篩選器加入至鏈結的命令篩選器。  
  
     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]  
  
4.  實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>觸發命令篩選條件時收到的簽章說明工作階段的方法 (一次的已知的方法名稱，並關閉工作階段，當它收到後的字元) 字元時仍在作用中工作階段。 在每個案例中，會轉送命令。  
  
     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]  
  
5.  實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法，使其永遠會轉送命令。  
  
     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>實作簽章說明命令提供者  
 您可以藉由實作中提供的簽章說明命令<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>文字檢視建立時，具現化的命令處理常式。  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>若要實作的簽章說明命令提供者  
  
1.  將類別命名為`TestSignatureHelpController`實作<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>並將它與匯出<xref:Microsoft.VisualStudio.Utilities.NameAttribute>， <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>，和<xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>。  
  
     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]  
  
2.  匯入<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>(用來取得<xref:Microsoft.VisualStudio.Text.Editor.ITextView>，並指定<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>物件)、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> （用來尋找目前的字組），而<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>（以觸發程序簽章說明工作階段）。  
  
     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]  
  
3.  實作<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A>方法藉由執行個體化`TestSignatureCommandHandler`。  
  
     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]  
  
## <a name="building-and-testing-the-code"></a>建置和測試程式碼  
 若要測試這段程式碼，建置 SignatureHelpTest 方案，並在實驗執行個體中執行。  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>若要建置和測試 SignatureHelpTest 方案  
  
1.  建置方案。  
  
2.  當您在偵錯工具中執行這個專案時，會具現化第二個 Visual Studio 執行個體。  
  
3.  建立文字檔案和一些文字，其中包含單字 「 加入 」 的型別加上左括號。  
  
4.  輸入左括號之後，您應該會看到工具提示會顯示一份兩個簽章`add()`方法。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說︰將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)