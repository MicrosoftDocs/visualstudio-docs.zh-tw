---
title: 逐步解說： 建立邊界字符 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 83b721c7b0ac33d9a37d9705cd780edcd591d9aa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490057"
---
# <a name="walkthrough-creating-a-margin-glyph"></a>逐步解說：建立邊界字符
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[逐步解說： 建立邊界圖像](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-creating-a-margin-glyph)。  
  
您可以使用自訂編輯器擴充功能，來自訂編輯器邊界的外觀。 本逐步解說會將自訂圖像 （glyph） 放在指示區邊界中，每當"todo"這個字出現在程式碼註解。  
  
## <a name="prerequisites"></a>必要條件  
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>建立 MEF 專案  
  
1.  建立 C# VSIX 專案。 (在**新的專案**對話方塊中，選取**Visual C# / 擴充性**，然後**VSIX 專案**。)將方案命名為`TodoGlyphTest`。  
  
2.  新增編輯器的分類器專案項目。 如需詳細資訊，請參閱 <<c0> [ 使用編輯器項目範本建立擴充](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  刪除現有類別檔案。  
  
## <a name="defining-the-glyph"></a>定義圖像 （glyph）  
 藉由實作定義圖像 （glyph）<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>介面。  
  
#### <a name="to-define-the-glyph"></a>若要定義圖像 （glyph）  
  
1.  將類別檔案並將它命名`TodoGlyphFactory`。  
  
2.  新增下列使用宣告。  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#1)]
     [!code-vb[VSSDKTodoGlyphTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#1)]  
  
3.  新增名為類別`TodoGlyphFactory`實作<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>。  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#2)]
     [!code-vb[VSSDKTodoGlyphTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#2)]  
  
4.  加入私用欄位來定義維度的圖像 （glyph）。  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#3)]
     [!code-vb[VSSDKTodoGlyphTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#3)]  
  
5.  實作`GenerateGlyph`藉由定義圖像 （glyph） 使用者介面 (UI) 項目。 `TodoTag` 在此逐步解說稍後定義。  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#4)]
     [!code-vb[VSSDKTodoGlyphTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#4)]  
  
6.  新增名為類別`TodoGlyphFactoryProvider`實作<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>。 匯出此類別<xref:Microsoft.VisualStudio.Utilities.NameAttribute>的 「 TodoGlyph"，<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>的後 VsTextMarker<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>的 「 程式碼 」 和<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>TodoTag。  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#5)]
     [!code-vb[VSSDKTodoGlyphTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#5)]  
  
7.  實作<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A>方法以具現化`TodoGlyphFactory`。  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#6)]
     [!code-vb[VSSDKTodoGlyphTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#6)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>定義 Todo 標記和標記者  
 藉由建立為標記類型和標記，並將它匯出使用標記者提供者定義上一個步驟中所定義的 UI 元素，並指示區邊界之間的關聯性。  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>若要定義的待辦事項標記和標記者  
  
1.  將新的類別檔案加入至專案並將它命名`TodoTagger`。  
  
2.  新增下列匯入。  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#7)]
     [!code-vb[VSSDKTodoGlyphTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#7)]  
  
3.  新增類別，名為`TodoTag`。  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#8)]
     [!code-vb[VSSDKTodoGlyphTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#8)]  
  
4.  修改名為的類別`TodoTagger`可實<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>型別的`TodoTag`。  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#9)]
     [!code-vb[VSSDKTodoGlyphTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#9)]  
  
5.  若要`TodoTagger`類別，新增私用欄位<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>和文字，以在分類中找到跨越。  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#10)]
     [!code-vb[VSSDKTodoGlyphTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#10)]  
  
6.  新增設定的分類器的建構函式。  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#11)]
     [!code-vb[VSSDKTodoGlyphTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#11)]  
  
7.  實作<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>找出所有分類的方法涵蓋其名稱包含"註解 」，以及其文字包含搜尋文字。 每當找到搜尋文字，則傳回產生的新<xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>型別的`TodoTag`。  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#12)]
     [!code-vb[VSSDKTodoGlyphTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#12)]  
  
8.  宣告`TagsChanged`事件。  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#13)]
     [!code-vb[VSSDKTodoGlyphTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#13)]  
  
9. 新增名為類別`TodoTaggerProvider`可實<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>，並將它與匯出<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>的 「 程式碼 」 和<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>TodoTag。  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#14)]
     [!code-vb[VSSDKTodoGlyphTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#14)]  
  
10. 匯入<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>。  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#15)]
     [!code-vb[VSSDKTodoGlyphTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#15)]  
  
11. 實作<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>方法以具現化`TodoTagger`。  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#16)]
     [!code-vb[VSSDKTodoGlyphTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#16)]  
  
## <a name="building-and-testing-the-code"></a>建置和測試程式碼  
 若要測試此程式碼，建置 TodoGlyphTest 方案，並在實驗執行個體中執行它。  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>若要建置和測試 TodoGlyphTest 方案  
  
1.  建置方案。  
  
2.  按 F5 執行專案。 Visual Studio 的第二個執行個體具現化。  
  
3.  請確定會顯示 指示區邊界。 (在**工具**功能表上，按一下**選項**。 在**文字編輯器**頁面上，請確定**指示區邊界**已選取。)  
  
4.  開啟具有註解的程式碼檔案。 將 word"todo"新增至其中一個註解區段。  
  
5.  指示區邊界的程式碼視窗左邊會出現具有深藍色外框的淺藍色圓形。

