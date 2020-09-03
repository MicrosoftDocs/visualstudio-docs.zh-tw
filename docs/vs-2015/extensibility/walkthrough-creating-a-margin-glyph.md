---
title: 逐步解說：建立邊界字型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa18b900ca44fbb52c646bfdf021beed6e77f504
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148850"
---
# <a name="walkthrough-creating-a-margin-glyph"></a>逐步解說：建立邊界字符
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用自訂編輯器延伸自訂編輯器邊界的外觀。 本逐步解說會在程式碼批註中出現 "todo" 一字時，將自訂圖像放在指標邊界上。  
  
## <a name="prerequisites"></a>Prerequisites  
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>建立 MEF 專案  
  
1. 建立 c # VSIX 專案。  (在 [ **新增專案** ] 對話方塊中，選取 [ **Visual c #/** 擴充性]，然後選取 [ **VSIX 專案**]。 ) 為方案命名 `TodoGlyphTest` 。  
  
2. 加入編輯器分類程式專案專案。 如需詳細資訊，請參閱 [使用編輯器專案範本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3. 刪除現有類別檔案。  
  
## <a name="defining-the-glyph"></a>定義圖像  
 藉由執行介面來定義圖像 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> 。  
  
#### <a name="to-define-the-glyph"></a>若要定義圖像  
  
1. 加入類別檔案，並將它命名為 `TodoGlyphFactory`。  
  
2. 使用宣告加入下列各項。  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#1)]
     [!code-vb[VSSDKTodoGlyphTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#1)]  
  
3. 加入名為 `TodoGlyphFactory` 的類別，該類別會執行 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> 。  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#2)]
     [!code-vb[VSSDKTodoGlyphTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#2)]  
  
4. 加入定義圖像尺寸的私用欄位。  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#3)]
     [!code-vb[VSSDKTodoGlyphTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#3)]  
  
5. 藉 `GenerateGlyph` 由定義圖像使用者介面 (UI) 元素來執行。 `TodoTag` 稍後會在本逐步解說中定義。  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#4)]
     [!code-vb[VSSDKTodoGlyphTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#4)]  
  
6. 加入名為 `TodoGlyphFactoryProvider` 的類別，該類別會執行 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> 。 使用 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph"、 <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> "VsTextMarker"、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "code" 和 of TodoTag 的來匯出這個類別 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> 。  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#5)]
     [!code-vb[VSSDKTodoGlyphTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#5)]  
  
7. 藉由具現 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> 化來執行方法 `TodoGlyphFactory` 。  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#6)]
     [!code-vb[VSSDKTodoGlyphTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#6)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>定義 Todo 標記和標記  
 藉由建立標記類型和標記，並使用標記提供者匯出，來定義您在前一個步驟中定義的 UI 元素與指標邊界之間的關聯性。  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>若要定義 todo 標記和標記  
  
1. 將新的類別檔案加入至專案，並將其命名為 `TodoTagger` 。  
  
2. 新增下列匯入。  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#7)]
     [!code-vb[VSSDKTodoGlyphTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#7)]  
  
3. 新增名為 `TodoTag`的類別。  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#8)]
     [!code-vb[VSSDKTodoGlyphTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#8)]  
  
4. 修改型別為 `TodoTagger` 之 implements 的類別 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> `TodoTag` 。  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#9)]
     [!code-vb[VSSDKTodoGlyphTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#9)]  
  
5. 針對 `TodoTagger` 類別，加入的私用欄位， <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 以及要在分類範圍中尋找的文字。  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#10)]
     [!code-vb[VSSDKTodoGlyphTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#10)]  
  
6. 加入設定分類器的函式。  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#11)]
     [!code-vb[VSSDKTodoGlyphTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#11)]  
  
7. 藉 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 由尋找所有分類範圍，其名稱中包含 "comment" 這個字，而其文字包含搜尋文字，來執行方法。 只要找到搜尋文字，就會傳回型別的新 <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> `TodoTag` 。  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#12)]
     [!code-vb[VSSDKTodoGlyphTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#12)]  
  
8. 宣告 `TagsChanged` 事件。  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#13)]
     [!code-vb[VSSDKTodoGlyphTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#13)]  
  
9. 加入名為的類別， `TodoTaggerProvider` 該類別 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> 會執行，並使用 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "code" 和 of <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag 來匯出。  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#14)]
     [!code-vb[VSSDKTodoGlyphTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#14)]  
  
10. 匯入 <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> 。  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#15)]
     [!code-vb[VSSDKTodoGlyphTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#15)]  
  
11. 藉由具現 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> 化來執行方法 `TodoTagger` 。  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#16)]
     [!code-vb[VSSDKTodoGlyphTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#16)]  
  
## <a name="building-and-testing-the-code"></a>建置和測試程式碼  
 若要測試此程式碼，請建立 TodoGlyphTest 方案，並在實驗實例中執行它。  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>若要建立及測試 TodoGlyphTest 方案  
  
1. 建置方案。  
  
2. 按下 F5 來執行專案。 Visual Studio 的第二個實例具現化。  
  
3. 請確定顯示的是指標邊界。  (在 [ **工具** ] 功能表上，按一下 [ **選項**]。 在 [ **文字編輯器** ] 頁面上，確認已選取 [ **指標邊界** ]。 )   
  
4. 開啟具有批註的程式碼檔案。 將 "todo" 這個字新增至其中一個批註區段。  
  
5. 具有深藍色外框的淺藍色圓形應該會出現在程式碼視窗左邊的指標邊界中。
