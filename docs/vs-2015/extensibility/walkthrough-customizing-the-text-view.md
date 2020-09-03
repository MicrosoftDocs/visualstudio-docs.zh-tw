---
title: 逐步解說：自訂文字視圖 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e96bb177d3cfa90b2c80304eabfd93d1bea76d5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202029"
---
# <a name="walkthrough-customizing-the-text-view"></a>逐步解說︰自訂文字檢視
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以在編輯器格式對應中修改下列任何屬性，以自訂文字視圖：  
  
- 指示區邊界  
  
- 插入插入號  
  
- 覆寫插入號  
  
- 選取的文字  
  
- 非使用中的選取文字 (也就是已遺失焦點的已選取文字)   
  
- 可見空白  
  
## <a name="prerequisites"></a>Prerequisites  
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>建立 MEF 專案  
  
1. 建立 c # VSIX 專案。  (在 [ **新增專案** ] 對話方塊中，選取 [ **Visual c #/** 擴充性]，然後選取 [ **VSIX 專案**]。 ) 為方案命名 `ViewPropertyTest` 。  
  
2. 將編輯器分類專案範本加入至專案。 如需詳細資訊，請參閱 [使用編輯器專案範本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3. 刪除現有類別檔案。  
  
## <a name="defining-the-content-type"></a>定義內容類型  
  
1. 加入類別檔案，並將它命名為 `ViewPropertyModifier`。  
  
2. 新增下列 `using` 指示詞：  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#1)]
    [!code-vb[VSSDKViewPropertyTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#1)]  
  
3. 宣告名為 `TestViewCreationListener` 的類別，該類別繼承自 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> 。 使用下列屬性匯出此類別：  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 指定此接聽程式套用的內容類型。  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> 指定此接聽程式的角色。  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#2)]
     [!code-vb[VSSDKViewPropertyTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#2)]  
  
4. 在這個類別中，匯入 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> 。  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#3)]
    [!code-vb[VSSDKViewPropertyTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#3)]  
  
## <a name="changing-the-view-properties"></a>變更視圖屬性  
  
1. 執行 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> 方法，以便在開啟視圖時變更視圖屬性。 若要進行變更，請先找出 <xref:System.Windows.ResourceDictionary> 對應到您想要尋找之觀點的。 然後變更資源字典中的適當屬性，並設定屬性。 藉由呼叫方法來批次處理方法的呼叫，然後再 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> 設定屬性，然後在 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> 設定屬性之後設定。  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#4)]
     [!code-vb[VSSDKViewPropertyTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#4)]  
  
## <a name="building-and-testing-the-code"></a>建置和測試程式碼  
  
1. 建置方案。  
  
     當您在偵錯工具中執行這個專案時，會具現化第二個 Visual Studio 執行個體。  
  
2. 建立文字檔，並輸入一些文字。  
  
    - 插入插入號應該是洋紅色，覆寫插入號應該是青。  
  
    - 文字視圖) 左邊的指標邊界 (應為淺綠色。  
  
3. 選取您剛剛輸入的文字。 所選文字的色彩應該是淺粉紅色。  
  
4. 選取文字時，請按一下文字視窗外的任何位置。 所選文字的色彩應該是深粉紅色。  
  
5. 開啟可見的空白。  (在 [ **編輯** ] 功能表上，指向 [ **Advanced** ]，然後按一下 [ **View** 空白字元]) 。 在文字中輸入一些索引標籤。 應該會顯示代表索引標籤的紅色箭號。  
  
## <a name="see-also"></a>另請參閱  
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
