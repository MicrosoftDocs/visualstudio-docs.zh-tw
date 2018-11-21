---
title: 逐步解說︰ 顯示簽章說明 |Microsoft Docs
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
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a3b902c32563da6bc21778a09b4aeaebaeabeaa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734635"
---
# <a name="walkthrough-displaying-signature-help"></a>逐步解說︰顯示簽章說明
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

簽章說明 (也稱為*參數資訊*) 方法的簽章顯示工具提示中，當使用者輸入的參數清單開始字元 （通常是左括號）。 依照所輸入的參數和參數分隔符號 （通常為逗號），工具提示會更新以顯示下一個參數以粗體顯示。 您可以定義簽章說明中的內容語言服務，或您可以定義您自己的檔案名稱擴充功能和內容類型，並顯示只是該類型的簽章說明或您可以顯示其簽章說明現有的內容類型 (例如，"text")。 本逐步解說示範如何以顯示簽章說明 「 文字 」 內容類型。  
  
 簽章說明通常會觸發輸入特定的字元，例如，"("（左括號），以及輸入另一個字元，例如已解除 」) 」 （右括號）。 IntelliSense 功能所觸發的輸入字元可以使用來實作命令處理常式的按鍵輸入 (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面) 和實作的處理常式提供者<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>介面。 若要建立簽章說明來源，也就是加入簽章說明中的簽章的清單，實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>介面和實作的來源提供者<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>介面。 提供者是 Managed Extensibility Framework (MEF) 元件組件，而且會負責將匯出的來源和控制器類別及匯入服務和代理程式，比方說， <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>，可以讓您在文字緩衝區中，瀏覽，<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>，此觸發程序的簽章說明工作階段。  
  
 本逐步解說示範如何實作簽章說明識別碼的硬式編碼集。 在完整的實作中，語言則是負責提供該內容項目。  
  
## <a name="prerequisites"></a>必要條件  
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>建立 MEF 專案  
  
#### <a name="to-create-a-mef-project"></a>建立 MEF 專案  
  
1.  建立 C# VSIX 專案。 (在**新的專案**對話方塊中，選取**Visual C# / 擴充性**，然後**VSIX 專案**。)將方案命名為 `SignatureHelpTest`。  
  
2.  將編輯器分類器項目範本加入專案。 如需詳細資訊，請參閱 <<c0> [ 使用編輯器項目範本建立擴充](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  刪除現有類別檔案。  
  
4.  將下列參考加入專案，並確認**CopyLocal**設定為`false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>實作簽章協助簽章和參數  
 簽章協助來源為基礎實作的簽章<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>，其中每一個包含實作的參數<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>。 在完整的實作中，這項資訊會取自語言文件中，但在此範例中，簽章是硬式編碼。  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>若要實作的簽章說明的簽章和參數  
  
1.  加入類別檔案，並將它命名為 `SignatureHelpSource`。  
  
2.  新增下列匯入。  
  
     [!code-csharp[VSSDKSignatureHelpTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#1)]
     [!code-vb[VSSDKSignatureHelpTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#1)]  
  
3.  新增名為類別`TestParameter`實作<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>。  
  
     [!code-csharp[VSSDKSignatureHelpTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#2)]
     [!code-vb[VSSDKSignatureHelpTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#2)]  
  
4.  新增將所有屬性的建構函式。  
  
     [!code-csharp[VSSDKSignatureHelpTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#3)]
     [!code-vb[VSSDKSignatureHelpTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#3)]  
  
5.  新增的屬性<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>。  
  
     [!code-csharp[VSSDKSignatureHelpTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#4)]
     [!code-vb[VSSDKSignatureHelpTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#4)]  
  
6.  新增名為類別`TestSignature`實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>。  
  
     [!code-csharp[VSSDKSignatureHelpTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#5)]
     [!code-vb[VSSDKSignatureHelpTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#5)]  
  
7.  加入一些私用欄位。  
  
     [!code-csharp[VSSDKSignatureHelpTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#6)]
     [!code-vb[VSSDKSignatureHelpTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#6)]  
  
8.  新增的建構函式設定的欄位，並訂閱<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>事件。  
  
     [!code-csharp[VSSDKSignatureHelpTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#7)]
     [!code-vb[VSSDKSignatureHelpTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#7)]  
  
9. 宣告`CurrentParameterChanged`事件。 當使用者填滿其中一種簽章中的參數時，會引發這個事件。  
  
     [!code-csharp[VSSDKSignatureHelpTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#8)]
     [!code-vb[VSSDKSignatureHelpTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#8)]  
  
10. 實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A>屬性，因此它會引發`CurrentParameterChanged`事件屬性值變更時。  
  
     [!code-csharp[VSSDKSignatureHelpTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#9)]
     [!code-vb[VSSDKSignatureHelpTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#9)]  
  
11. 新增方法以引發`CurrentParameterChanged`事件。  
  
     [!code-csharp[VSSDKSignatureHelpTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#10)]
     [!code-vb[VSSDKSignatureHelpTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#10)]  
  
12. 新增方法，藉由比較中的逗號數目來計算目前參數<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>簽章中的逗號數目。  
  
     [!code-csharp[VSSDKSignatureHelpTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#11)]
     [!code-vb[VSSDKSignatureHelpTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#11)]  
  
13. 新增事件處理常式<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>呼叫的事件`ComputeCurrentParameter()`方法。  
  
     [!code-csharp[VSSDKSignatureHelpTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#12)]
     [!code-vb[VSSDKSignatureHelpTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#12)]  
  
14. 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> 屬性。 此屬性會保留<xref:Microsoft.VisualStudio.Text.ITrackingSpan>對應的簽章套用至緩衝區中的文字範圍。  
  
     [!code-csharp[VSSDKSignatureHelpTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#13)]
     [!code-vb[VSSDKSignatureHelpTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#13)]  
  
15. 實作其他參數。  
  
     [!code-csharp[VSSDKSignatureHelpTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#14)]
     [!code-vb[VSSDKSignatureHelpTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#14)]  
  
## <a name="implementing-the-signature-help-source"></a>實作簽章說明來源  
 簽章說明來源是您要為其提供資訊的簽章組。  
  
#### <a name="to-implement-the-signature-help-source"></a>若要實作的簽章說明來源  
  
1.  新增名為類別`TestSignatureHelpSource`實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>。  
  
     [!code-csharp[VSSDKSignatureHelpTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#15)]
     [!code-vb[VSSDKSignatureHelpTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#15)]  
  
2.  加入至文字的緩衝區的參考。  
  
     [!code-csharp[VSSDKSignatureHelpTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#16)]
     [!code-vb[VSSDKSignatureHelpTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#16)]  
  
3.  新增設定文字緩衝區和簽章說明來源提供者的建構函式。  
  
     [!code-csharp[VSSDKSignatureHelpTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#17)]
     [!code-vb[VSSDKSignatureHelpTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#17)]  
  
4.  實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> 方法。 在此範例中，簽章是以硬式編碼，但完整的實作中您會從語言文件取得這項資訊。  
  
     [!code-csharp[VSSDKSignatureHelpTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#18)]
     [!code-vb[VSSDKSignatureHelpTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#18)]  
  
5.  Helper 方法`CreateSignature()`提供僅供說明。  
  
     [!code-csharp[VSSDKSignatureHelpTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#19)]
     [!code-vb[VSSDKSignatureHelpTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#19)]  
  
6.  實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> 方法。 在此範例中，有兩個簽章，每個都有兩個參數。 因此，這個方法不需要。 在更完整的實作中，在其中多個簽章說明來源可供使用，這個方法用來決定最高優先順序簽章說明來源是否可以提供相符的簽章。 如果不行，方法會傳回 null，並提供符合項目要求的下一個最高優先順序的來源。  
  
     [!code-csharp[VSSDKSignatureHelpTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#20)]
     [!code-vb[VSSDKSignatureHelpTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#20)]  
  
7.  實作 dispose （） 方法：  
  
     [!code-csharp[VSSDKSignatureHelpTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#21)]
     [!code-vb[VSSDKSignatureHelpTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#21)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>實作簽章說明來源提供者  
 簽章說明來源提供者是負責匯出 Managed Extensibility Framework (MEF) 元件組件，以及具現化的簽章說明來源。  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>若要實作的簽章說明來源提供者  
  
1.  新增名為的類別`TestSignatureHelpSourceProvider`可實<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>，並將它與匯出<xref:Microsoft.VisualStudio.Utilities.NameAttribute>，則<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>為"text"，和<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>的 Before ="default"。  
  
     [!code-csharp[VSSDKSignatureHelpTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#22)]
     [!code-vb[VSSDKSignatureHelpTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#22)]  
  
2.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A>具現化`TestSignatureHelpSource`。  
  
     [!code-csharp[VSSDKSignatureHelpTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#23)]
     [!code-vb[VSSDKSignatureHelpTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#23)]  
  
## <a name="implementing-the-command-handler"></a>實作命令處理常式  
 簽章說明通常會觸發 (字元和已解除的) 字元。 您可以藉由實作來處理這些按鍵<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>以便觸發當它收到的簽章說明工作階段 (字元加上已知的方法名稱，並關閉工作階段，當它收到) 字元。  
  
#### <a name="to-implement-the-command-handler"></a>若要實作的命令處理常式  
  
1.  新增名為類別`TestSignatureHelpCommand`實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
     [!code-csharp[VSSDKSignatureHelpTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#24)]
     [!code-vb[VSSDKSignatureHelpTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#24)]  
  
2.  新增私用欄位<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>配接器 （可讓您將命令處理常式新增至鏈結的命令處理常式）、 [文字] 檢視、 簽章說明中的訊息代理程式和工作階段中， <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>，和 [下一步] <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
     [!code-csharp[VSSDKSignatureHelpTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#25)]
     [!code-vb[VSSDKSignatureHelpTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#25)]  
  
3.  加入建構函式來初始化這些欄位，並將命令篩選器新增至鏈結的命令篩選器。  
  
     [!code-csharp[VSSDKSignatureHelpTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#26)]
     [!code-vb[VSSDKSignatureHelpTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#26)]  
  
4.  實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>方法來觸發命令篩選器時收到的簽章說明工作階段 (一個已知的方法名稱，並關閉工作階段，當它收到一次之後的字元) 字元仍在作用中工作階段時。 在每個案例中，會轉送命令。  
  
     [!code-csharp[VSSDKSignatureHelpTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#27)]
     [!code-vb[VSSDKSignatureHelpTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#27)]  
  
5.  實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法，讓它一律會將轉送的命令。  
  
     [!code-csharp[VSSDKSignatureHelpTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#28)]
     [!code-vb[VSSDKSignatureHelpTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#28)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>實作簽章說明命令提供者  
 您可以藉由實作提供的簽章說明命令<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>建立文字檢視時，具現化的命令處理常式。  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>若要實作的簽章說明命令提供者  
  
1.  新增名為類別`TestSignatureHelpController`可實<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>並將它與匯出<xref:Microsoft.VisualStudio.Utilities.NameAttribute>， <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>，和<xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>。  
  
     [!code-csharp[VSSDKSignatureHelpTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#29)]
     [!code-vb[VSSDKSignatureHelpTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#29)]  
  
2.  匯入<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>(用來取得<xref:Microsoft.VisualStudio.Text.Editor.ITextView>，給定<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>物件)，則<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>（用來尋找目前的字組），而<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>（以觸發簽章說明工作階段）。  
  
     [!code-csharp[VSSDKSignatureHelpTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#30)]
     [!code-vb[VSSDKSignatureHelpTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#30)]  
  
3.  實作<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A>方法以具現化`TestSignatureCommandHandler`。  
  
     [!code-csharp[VSSDKSignatureHelpTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#31)]
     [!code-vb[VSSDKSignatureHelpTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#31)]  
  
## <a name="building-and-testing-the-code"></a>建置和測試程式碼  
 若要測試此程式碼，建置 SignatureHelpTest 方案，並在實驗執行個體中執行它。  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>若要建置和測試 SignatureHelpTest 方案  
  
1.  建置方案。  
  
2.  當您在偵錯工具中執行這個專案時，會具現化第二個 Visual Studio 執行個體。  
  
3.  建立文字檔案和一些文字，其中包含單字"add"的類型加上左括號。  
  
4.  輸入左括號之後，您應該會看到工具提示會顯示一份兩個簽章`add()`方法。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說︰將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

