---
title: "逐步解說︰ 顯示簽章說明 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，新的簽章說明/參數資訊"
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# 逐步解說︰ 顯示簽章說明
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

簽章說明 \(也稱為 *參數資訊*\) 時，顯示方法的簽章工具提示使用者輸入的參數清單開始字元 （通常是左括號）。 輸入的參數和參數分隔符號 （通常是逗號），工具提示會更新以顯示下一個參數以粗體顯示。 您可以定義的語言服務內容中的 「 簽章說明您可以定義您的檔案名稱副檔名和內容類型，只要該類型，顯示 \[簽章說明或現有的內容類型 （例如，「 文字 」） 可以顯示 \[簽章說明。 本逐步解說示範如何顯示簽章說明 「 文字 」 內容類型。  
  
 簽章說明通常會觸發輸入特定字元，例如，「 \(」 （左括號），並解除輸入另一個字元，例如，「\) 」 （右括號）。 使用按鍵輸入的命令處理常式，即可實作所觸發的輸入字元的 IntelliSense 功能 \( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面\) 和處理常式提供者實作 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 介面。 若要建立簽章說明來源，這是參與協助簽章的簽章的清單，實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> 介面和實作的來源提供者 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> 介面。 提供者是 Managed Extensibility Framework \(MEF\) 元件組件，而且負責匯出的來源和控制器類別和匯入服務和代理程式，例如 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, ，可讓您在文字緩衝區中，瀏覽和 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, ，而觸發的簽章說明工作階段。  
  
 本逐步解說示範如何實作簽章說明硬式編碼的識別項組。 在完整的實作中，語言會負責將該內容。  
  
## 必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 建立 MEF 專案  
  
#### 建立 MEF 專案  
  
1.  建立 C\# VSIX 專案。 \(在 **新的專案** 對話方塊中，選取 **Visual C\# \/ 擴充性**, ，然後 **VSIX 專案**。\) 將方案命名為 `SignatureHelpTest`。  
  
2.  將編輯器分類項目範本加入至專案。 如需詳細資訊，請參閱[使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  刪除現有類別檔案。  
  
4.  將下列參考加入專案，並確認 **CopyLocal** 設為 `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## 實作簽章協助簽章和參數  
 簽章說明來源為基礎實作的簽章 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, ，其中每個包含可實作參數 <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>。 在完整的實作，這項資訊會取自語言文件，但在此範例中，簽章是硬式編碼。  
  
#### 若要實作的簽章說明簽章和參數  
  
1.  將類別檔案，並將它 `SignatureHelpSource`。  
  
2.  新增下列匯入。  
  
     [!CODE [VSSDKSignatureHelpTest#1](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#1)]  
  
3.  新增名為 `TestParameter` 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>。  
  
     [!CODE [VSSDKSignatureHelpTest#2](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#2)]  
  
4.  加入將所有屬性的建構函式。  
  
     [!CODE [VSSDKSignatureHelpTest#3](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#3)]  
  
5.  新增的屬性 <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>。  
  
     [!CODE [VSSDKSignatureHelpTest#4](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#4)]  
  
6.  新增名為 `TestSignature` 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>。  
  
     [!CODE [VSSDKSignatureHelpTest#5](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#5)]  
  
7.  加入一些私用欄位。  
  
     [!CODE [VSSDKSignatureHelpTest#6](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#6)]  
  
8.  新增的建構函式，設定欄位，以及訂閱 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 事件。  
  
     [!CODE [VSSDKSignatureHelpTest#7](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#7)]  
  
9. 宣告 `CurrentParameterChanged` 事件。 當使用者填其中一種簽章中的參數時，會引發這個事件。  
  
     [!CODE [VSSDKSignatureHelpTest#8](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#8)]  
  
10. 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> 屬性，好，就會引發 `CurrentParameterChanged` 事件屬性值變更時。  
  
     [!CODE [VSSDKSignatureHelpTest#9](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#9)]  
  
11. 新增方法以引發 `CurrentParameterChanged` 事件。  
  
     [!CODE [VSSDKSignatureHelpTest#10](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#10)]  
  
12. 加入的方法，藉由比較中的逗號分隔的數字會計算目前參數 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> 簽章中的逗號分隔的數字。  
  
     [!CODE [VSSDKSignatureHelpTest#11](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#11)]  
  
13. 加入事件處理常式 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 事件呼叫 `ComputeCurrentParameter()` 方法。  
  
     [!CODE [VSSDKSignatureHelpTest#12](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#12)]  
  
14. 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> 屬性。 這個屬性會保留 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 對應的簽章套用至緩衝區中的文字範圍的。  
  
     [!CODE [VSSDKSignatureHelpTest#13](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#13)]  
  
15. 實作其他參數。  
  
     [!CODE [VSSDKSignatureHelpTest#14](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#14)]  
  
## 實作的簽章說明來源  
 簽章說明來源是您要為其提供資訊的簽章組。  
  
#### 若要實作的簽章說明來源  
  
1.  新增名為 `TestSignatureHelpSource` 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>。  
  
     [!CODE [VSSDKSignatureHelpTest#15](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#15)]  
  
2.  加入文字緩衝區的參考。  
  
     [!CODE [VSSDKSignatureHelpTest#16](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#16)]  
  
3.  新增設定文字緩衝區和簽章說明來源提供者的建構函式。  
  
     [!CODE [VSSDKSignatureHelpTest#17](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#17)]  
  
4.  實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> 方法。 在此範例中，簽章是硬式編碼，但在完整的實作中您會從語言文件取得此資訊。  
  
     [!CODE [VSSDKSignatureHelpTest#18](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#18)]  
  
5.  Helper 方法 `CreateSignature()` 只供示範。  
  
     [!CODE [VSSDKSignatureHelpTest#19](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#19)]  
  
6.  實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> 方法。 在此範例中，有兩個簽章，每一個都有兩個參數。 因此，這個方法不需要。 在更完整的實作中，多個簽章說明來源可以使用，這個方法用來決定最高優先權簽章說明來源是否可以提供相符的簽章。 如果不行，此方法會傳回 null 下, 一個最高優先順序的來源必須提供相符項目。  
  
     [!CODE [VSSDKSignatureHelpTest#20](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#20)]  
  
7.  實作 dispose （） 方法︰  
  
     [!CODE [VSSDKSignatureHelpTest#21](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#21)]  
  
## 實作的簽章說明來源提供者  
 簽章說明來源提供者是負責匯出 Managed Extensibility Framework \(MEF\) 元件組件，以及具現化的簽章說明來源。  
  
#### 若要實作的簽章說明來源提供者  
  
1.  新增名為 `TestSignatureHelpSourceProvider` 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>, ，並將它與匯出 <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, 、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 的 「 文字 」，和 <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> 的之前 \="default"。  
  
     [!CODE [VSSDKSignatureHelpTest#22](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#22)]  
  
2.  實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> 藉由執行個體化 `TestSignatureHelpSource`。  
  
     [!CODE [VSSDKSignatureHelpTest#23](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#23)]  
  
## 實作命令處理常式  
 簽章說明通常會觸發 \(字元和已解除的\) 字元。 您可以藉由實作來處理這些按鍵 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ，讓它觸發當它收到的簽章說明工作階段 \(字元前面加上已知的方法名稱，並解除工作階段，當它收到\) 字元。  
  
#### 若要實作的命令處理常式  
  
1.  新增名為 `TestSignatureHelpCommand` 實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
     [!CODE [VSSDKSignatureHelpTest#24](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#24)]  
  
2.  加入私用欄位 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 介面卡 （這可讓您將命令處理常式加入至鏈結的命令處理常式）、 文字檢視、 簽章說明代理人和工作階段， <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, ，和下 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
     [!CODE [VSSDKSignatureHelpTest#25](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#25)]  
  
3.  新增的建構函式來初始化這些欄位，並將命令篩選器新增至鏈結的命令篩選器。  
  
     [!CODE [VSSDKSignatureHelpTest#26](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#26)]  
  
4.  實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法來觸發命令篩選器時收到的簽章說明工作階段 \(一個已知的方法名稱，並關閉工作階段，當它收到之後的字元\) 字元時仍在作用中工作階段。 在每個案例中，便會轉送命令。  
  
     [!CODE [VSSDKSignatureHelpTest#27](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#27)]  
  
5.  實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法，使它一定會轉送命令。  
  
     [!CODE [VSSDKSignatureHelpTest#28](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#28)]  
  
## 實作簽章說明命令提供者  
 您可以藉由實作提供簽章說明命令 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 來建立文字檢視時，具現化的命令處理常式。  
  
#### 若要實作的簽章說明命令提供者  
  
1.  新增名為 `TestSignatureHelpController` 實作 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 並將它與匯出 <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, ，<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, ，和 <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>。  
  
     [!CODE [VSSDKSignatureHelpTest#29](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#29)]  
  
2.  匯入 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> \(用來取得 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, 、 指定 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 物件\)、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> （用來尋找目前的文字），而 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> （若要觸發簽章說明工作階段）。  
  
     [!CODE [VSSDKSignatureHelpTest#30](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#30)]  
  
3.  實作 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> 方法具現化 `TestSignatureCommandHandler`。  
  
     [!CODE [VSSDKSignatureHelpTest#31](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#31)]  
  
## 建置和測試程式碼  
 若要測試這段程式碼，SignatureHelpTest 方案中建置並執行它的實驗執行個體。  
  
#### 若要建置和測試 SignatureHelpTest 方案  
  
1.  建置方案。  
  
2.  當您在偵錯工具中執行這個專案時，會具現化第二個 Visual Studio 執行個體。  
  
3.  建立文字檔案和一些文字，其中包含單字"add"的類型加上左括號。  
  
4.  輸入左括號之後，您應該會看到工具提示會顯示一份兩個簽章 `add()` 方法。  
  
## 請參閱  
 [逐步解說: 將內容類型連結至檔案名稱副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)