---
title: 逐步解說：顯示智慧標籤 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - smart tags
ms.assetid: 10bb4f69-b259-41f0-b91a-69b04385d9a5
caps.latest.revision: 31
manager: jillfra
ms.openlocfilehash: a14fcb8e81261962e8851347a54d7c8d52565d20
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110436"
---
# <a name="walkthrough-displaying-smarttags"></a>逐步解說：顯示智慧標籤
智慧標籤已取代為燈泡。 請參閱[逐步解說：Displaying Light Bulb Suggestions](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)。  
  
 智慧標籤是文字上展開以顯示一組動作的標籤。 例如，在 Visual Basic 或 Visual C# 專案中，當您重新命名識別項 (例如變數名稱) 時，會在這個字組下方出現紅線。 當您將指標移至底線上方時，會在指標附近顯示按鈕。 如果您按一下該按鈕，則會顯示建議的動作 (例如，[將 IsRead 重新命名為 IsReady] )。 如果您按一下該動作，專案中的所有 **IsRead** 參考都會重新命名為 **IsReady**。  
  
 雖然智慧標籤是編輯器中 IntelliSense 實作的一部分，但是您可以透過子類別化 <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>，然後實作 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 介面和 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> 介面，來實作智慧標籤。  
  
> [!NOTE]
>  其他類型的標籤可以透過類似的方式實作。  
  
 下列逐步解說示範如何建立智慧標籤會出現在目前的文字，有兩個建議的動作：**轉換為大寫**並**轉換為小寫**。  
  
## <a name="prerequisites"></a>必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 < [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>建立 MEF 專案  
  
1. 建立編輯器分類器專案。 將方案命名為 `SmartTagTest`。  
  
2. 在 VSIX 資訊清單編輯器中，開啟 source.extension.vsixmanifest 檔案。  
  
3. 確定 [資產]  區段包含 `Microsoft.VisualStudio.MefComponent` 類型、[來源]  設定為 `A project in current solution`，並將 [專案]  設定為 SmartTagTest.dll。  
  
4. 儲存並關閉 source.extension.vsixmanifest。  
  
5. 將下列參考加入專案中，並將 **CopyLocal** 設定為 `false`：  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
6. 刪除現有類別檔案。  
  
## <a name="implementing-a-tagger-for-smart-tags"></a>實作智慧標籤的標記者  
  
#### <a name="to-implement-a-tagger-for-smart-tags"></a>實作智慧標籤的標記者  
  
1. 加入類別檔案，並將它命名為 `TestSmartTag`。  
  
2. 加入下列匯入：  
  
     [!code-csharp[VSSDKSmartTagTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#1)]
     [!code-vb[VSSDKSmartTagTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#1)]  
  
3. 加入名為 `TestSmartTag` 且繼承自 <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> 的類別。  
  
     [!code-csharp[VSSDKSmartTagTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#2)]
     [!code-vb[VSSDKSmartTagTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#2)]  
  
4. 加入這個類別的建構函式，以使用 <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> 的 <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> 來呼叫基底建構函式，這樣會在某個字組的第一個字元下方出現藍線。  (如果您使用 <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>，會在這個字組的最後一個字元下方出現紅線)。  
  
     [!code-csharp[VSSDKSmartTagTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#3)]
     [!code-vb[VSSDKSmartTagTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#3)]  
  
5. 加入名為 `TestSmartTagger` 的類別，這個類別繼承自類型 `TestSmartTag` 的 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>，並實作 <xref:System.IDisposable>。  
  
     [!code-csharp[VSSDKSmartTagTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#4)]
     [!code-vb[VSSDKSmartTagTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#4)]  
  
6. 在標記者類別中加入下列私用欄位。  
  
     [!code-csharp[VSSDKSmartTagTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#5)]
     [!code-vb[VSSDKSmartTagTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#5)]  
  
7. 加入建構函式，以設定私用欄位並訂閱 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> 事件。  
  
     [!code-csharp[VSSDKSmartTagTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#6)]
     [!code-vb[VSSDKSmartTagTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#6)]  
  
8. 實作 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>，以為目前字組建立標籤。 (這種方法也會呼叫稍後說明的私用方法 `GetSmartTagActions` )。  
  
     [!code-csharp[VSSDKSmartTagTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#7)]
     [!code-vb[VSSDKSmartTagTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#7)]  
  
9. 加入 `GetSmartTagActions` 方法來設定智慧標籤動作。 在後面的步驟中會實作動作本身。  
  
     [!code-csharp[VSSDKSmartTagTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#8)]
     [!code-vb[VSSDKSmartTagTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#8)]  
  
10. 宣告 `SmartTagsChanged` 事件。  
  
     [!code-csharp[VSSDKSmartTagTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#9)]
     [!code-vb[VSSDKSmartTagTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#9)]  
  
11. 實作 `OnLayoutChanged` 事件處理常式來引發 `TagsChanged` 事件，以呼叫 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>。  
  
     [!code-csharp[VSSDKSmartTagTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#10)]
     [!code-vb[VSSDKSmartTagTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#10)]  
  
12. 實作 <xref:System.IDisposable.Dispose%2A> 方法，以從 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> 事件中取消訂閱它。  
  
     [!code-csharp[VSSDKSmartTagTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#11)]
     [!code-vb[VSSDKSmartTagTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#11)]  
  
## <a name="implementing-the-smart-tag-tagger-provider"></a>實作智慧標籤標記者提供者  
  
#### <a name="to-implement-the-smart-tag-tagger-provider"></a>實作智慧標籤標記者提供者  
  
1. 加入名為 `TestSmartTagTaggerProvider` 且繼承自 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> 的類別。 使用 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 為 "text"、<xref:Microsoft.VisualStudio.Utilities.OrderAttribute> 為 Before="default" 且 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> 為 <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>，來匯出它。  
  
     [!code-csharp[VSSDKSmartTagTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#12)]
     [!code-vb[VSSDKSmartTagTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#12)]  
  
2. 匯入 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> 作為屬性。  
  
     [!code-csharp[VSSDKSmartTagTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#13)]
     [!code-vb[VSSDKSmartTagTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#13)]  
  
3. 實作 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> 方法。  
  
     [!code-csharp[VSSDKSmartTagTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#14)]
     [!code-vb[VSSDKSmartTagTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#14)]  
  
## <a name="implementing-smart-tag-actions"></a>實作智慧標籤動作  
  
#### <a name="to-implement-smart-tag-actions"></a>實作智慧標籤動作  
  
1. 建立兩個類別：第一個命名為 `UpperCaseSmartTagAction` ，第二個則命名為 `LowerCaseSmartTagAction`。 這兩個類別都會實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction>。  
  
    [!code-csharp[VSSDKSmartTagTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#15)]
    [!code-vb[VSSDKSmartTagTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#15)]  
  
    [!code-csharp[VSSDKSmartTagTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#16)]
    [!code-vb[VSSDKSmartTagTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#16)]  
  
   這兩個類別相同，差別在於其中一個會呼叫 <xref:System.String.ToUpper%2A>，另一個會呼叫 <xref:System.String.ToLower%2A>。 下列步驟僅涵蓋大寫動作類別，但您必須實作這兩個類別。 使用實作大寫動作的步驟，作為實作小寫動作的模式。  
  
2. 宣告一組私用欄位。  
  
    [!code-csharp[VSSDKSmartTagTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#17)]
    [!code-vb[VSSDKSmartTagTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#17)]  
  
3. 加入可設定欄位的建構函式。  
  
    [!code-csharp[VSSDKSmartTagTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#18)]
    [!code-vb[VSSDKSmartTagTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#18)]  
  
4. 依照下列所示來實作屬性。  
  
    [!code-csharp[VSSDKSmartTagTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#19)]
    [!code-vb[VSSDKSmartTagTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#19)]  
  
5. 將範圍中的文字取代為其大寫對等項目，以實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction.Invoke%2A> 方法。  
  
    [!code-csharp[VSSDKSmartTagTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#20)]
    [!code-vb[VSSDKSmartTagTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#20)]  
  
## <a name="building-and-testing-the-code"></a>建置和測試程式碼  
 若要測試這段程式碼，請建置 SmartTagTest 方案，並在實驗執行個體中執行它。  
  
#### <a name="to-build-and-test-the-smarttagtest-solution"></a>建置並測試 SmartTagTest 方案  
  
1. 建置方案。  
  
2. 當您在偵錯工具中執行這個專案時，會具現化第二個 Visual Studio 執行個體。  
  
3. 建立文字檔，並輸入一些文字。  
  
     應該會在文字之第一個字組的第一個字母下方顯示藍線。  
  
4. 將指標移至藍線上方。  
  
     應該會在指標附近顯示按鈕。  
  
5. 當您按一下按鈕時，應該會顯示兩個建議的動作：**轉換為大寫**並**轉換為小寫**。 如果您按一下第一個動作，則應該會將目前字組中的所有文字都轉換為大寫。 如果您按一下第二個動作，則應該會將所有文字都轉換為小寫。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)