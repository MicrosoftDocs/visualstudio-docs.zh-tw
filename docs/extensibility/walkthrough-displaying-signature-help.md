---
title: 演練:顯示簽名説明 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f85d7eb3959064468e7583ec0c8a927f3e139daf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697424"
---
# <a name="walkthrough-display-signature-help"></a>演練:顯示簽名說明
當使用者鍵入參數清單開始字元(通常是打開括弧)時,簽名説明(也稱為*參數資訊*)在工具提示中顯示方法的簽名。 當鍵入參數和參數分隔符(通常是逗號)時,工具提示將更新以粗體顯示下一個參數。 您可以通過以下方式定義簽名説明:在語言服務的上下文中,定義您自己的檔案名擴展名和內容類型,並僅顯示該類型的簽名説明,或顯示現有內容類型的簽名説明(例如,"文本")。 本演練演示如何顯示"文本"內容類型的簽名説明。

 簽名説明通常通過鍵入特定字元(例如"("("(打開括弧))觸發,並通過鍵入另一個字元(例如")"(關閉括弧)來消除。 通過鍵入字元觸發的 IntelliSense 功能可以通過使用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>擊鍵( 介面)的命令處理程式<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>和實現介面的 處理程式提供程式實現。 要建立簽名説明源(即參與簽名幫助的簽名清單),請實現<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>介面和運行該介面的<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>源提供程式。 提供程式是託管延伸框架 (MEF) 元件,負責匯出來源和控制器類別以及匯入服務和代理,例如,允許您在文字緩衝區中導航的<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>與觸發簽署說明工作階段的<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>。

 本演練演示如何為硬編碼的標識符集設置簽名説明。 在完全實現中,語言負責提供該內容。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="creating-a-mef-project"></a>建立 MEF 專案

#### <a name="to-create-a-mef-project"></a>建立 MEF 專案

1. 創建 C# VSIX 專案。 ( 在 **'新增項目'** 對話框中,選擇**視覺化 C# / 可擴充性**,然後選擇**VSIX 專案**。命名解決方案`SignatureHelpTest`。

2. 加入專案加入編輯器分類器項範本。 關於詳細資訊,請參考[使用編輯器項目樣本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3. 刪除現有類別檔案。

4. 新增對專案的以下參考,並確保**CopyLocal**`false`設定為 :

     微軟.VisualStudio.編輯器

     Microsoft.VisualStudio.Language.Intellisense

     微軟.VisualStudio.OLE.Interop

     微軟.VisualStudio.shell.14.0

     微軟.VisualStudio.文字管理員.互通

## <a name="implement-signature-help-signatures-and-parameters"></a>取得簽署簽名與參數
 簽名説明源基於實現<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>的簽名,每個簽名都包含實現<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>的參數。 在完全實現中,此資訊將從語言文檔獲得,但在此示例中,簽名是硬編碼的。

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>取得簽署簽名與參數

1. 加入類別檔案，並將它命名為 `SignatureHelpSource`。

2. 新增下列匯入。

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3. 新增名為`TestParameter`的類別<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>,實現 。

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4. 添加設置所有屬性的構造函數。

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5. 新增的屬性<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>。

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6. 新增名為`TestSignature`的類別<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>,實現 。

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7. 添加一些私有欄位。

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8. 新增建構函數,用於設定欄位並訂閱事件<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>。

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. 宣告事件`CurrentParameterChanged`。 當使用者填寫簽名中的一個參數時,將引發此事件。

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. 實現該<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A>屬性,以便在更改屬性`CurrentParameterChanged`值 時引發事件。

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. 添加引發`CurrentParameterChanged`事件的方法。

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. 添加一個計算當前參數的方法,方法是將 中的逗<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>號 數與簽名中的逗號數進行比較。

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. 為調用<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>`ComputeCurrentParameter()`該方法的事件添加事件處理程式。

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> 屬性。 此屬性儲存與簽署<xref:Microsoft.VisualStudio.Text.ITrackingSpan>套用的緩衝區中的文字範圍對應的 。

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. 實現其他參數。

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>取得簽署說明來源
 簽名説明來源是您為其提供資訊的簽名集。

#### <a name="to-implement-the-signature-help-source"></a>取得簽署說明來源

1. 新增名為`TestSignatureHelpSource`的類別<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>,實現 。

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2. 添加對文字緩衝區的引用。

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3. 新增設置文本緩衝區和簽名説明源提供程式的構造函數。

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4. 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> 方法。 這個選項,簽名是硬編碼的,但在完全實現中,您將從語言文件中獲取此資訊。

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5. 幫助器方法`CreateSignature()`僅供說明。

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6. 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> 方法。 在此示例中,只有兩個簽名,每個簽名都有兩個參數。 因此,此方法不是必需的。 在具有多個簽名説明源的更完整實現中,此方法用於決定優先順序最高的簽名説明源是否可以提供匹配的簽名。 如果不能,該方法將返回 null,並且要求下一個優先順序最高的源提供匹配項。

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7. 實作`Dispose()`方法 :

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>提供簽署說明來源提供者
 簽名説明源提供程式負責匯出託管擴展框架 (MEF) 元件部分並實例化簽名説明源。

#### <a name="to-implement-the-signature-help-source-provider"></a>提供簽署說明來源提供者

1. 添加名為`TestSignatureHelpSourceProvider`的<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>類, 實現 ,<xref:Microsoft.VisualStudio.Utilities.NameAttribute>並<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>匯出它 與<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>的 「文本」和 前 = "預設值"。

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2. 透過<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A>實體化 實`TestSignatureHelpSource`例化 。

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>執行命令處理程式
 簽名説明通常由開放括號「(」字元)觸發,並通過關閉括弧")"字元關閉。 可以通過運行<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>來處理 這些擊鍵,以便在它收到打開的括弧字元之前具有已知方法名稱時觸發簽名説明會話,並在會話收到關閉的括弧字元時將其關閉。

#### <a name="to-implement-the-command-handler"></a>執行命令處理程式

1. 新增名為`TestSignatureHelpCommand`的類別<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>,實現 。

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2. 新增<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>私密字段(允許您將指令處理程式來新增指令處理程式鍊,文字檢視、簽署說明代理與工作階段、下<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>一個<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3. 添加建構函數來初始化這些欄位,並將命令篩選器添加到命令篩選器鏈中。

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4. 實現<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>方法在命令篩選器收到一個已知方法名稱後的開放括弧」。(")字元時觸發簽名説明會話;並在會話仍然處於活動狀態時收到關閉括弧")字元時關閉會話」。 在每種情況下,命令都會被轉發。

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5. 實現該方法<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>,以便它始終轉發命令。

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>提供簽署說明指令提供者
 可以通過在創建文本檢視時實現實例化命令<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>處理程式來提供簽名説明命令。

### <a name="to-implement-the-signature-help-command-provider"></a>提供簽署說明指令提供者

1. 新增名為的`TestSignatureHelpController`類別,<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>該類別會匯出<xref:Microsoft.VisualStudio.Utilities.NameAttribute><xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>。<xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2. 匯入<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>(<xref:Microsoft.VisualStudio.Text.Editor.ITextView>用於<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>取得給定物件)、(<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>用於搜尋目前單字)<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>和 (用於觸發簽名幫助會話)。

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3. 通過實例<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A>化`TestSignatureCommandHandler`實現 方法。

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>組建及測試代碼
 要測試此代碼,請構建簽名幫助測試解決方案並在實驗實例中運行它。

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>建構並測試簽章說明測試解決方案

1. 建置方案。

2. 在除錯器中執行此專案時,將啟動 Visual Studio 的第二個實體。

3. 建立文字檔並鍵入一些包含單詞"add"加上開口括弧的文本。

4. 鍵入打開括弧後,應看到一個工具提示,顯示`add()`該方法的兩個簽名的清單。

## <a name="see-also"></a>另請參閱
- [演練:將內容類型連結到檔案名副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
