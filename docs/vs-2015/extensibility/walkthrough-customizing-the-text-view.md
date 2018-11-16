---
title: 逐步解說： 自訂文字檢視 |Microsoft Docs
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
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 38cbd0117f5f49666ee5da42d0f60dadf451ffda
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781812"
---
# <a name="walkthrough-customizing-the-text-view"></a>逐步解說︰自訂文字檢視
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以自訂文字檢視，方法是修改任何它的編輯器格式對應中的下列屬性：  
  
-   指示區邊界  
  
-   插入號  
  
-   覆寫插入號  
  
-   選取的文字  
  
-   非現用選取的文字 （也就是選取的文字已遺失焦點）  
  
-   可見的空白字元  
  
## <a name="prerequisites"></a>必要條件  
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>建立 MEF 專案  
  
1.  建立 C# VSIX 專案。 (在**新的專案**對話方塊中，選取**Visual C# / 擴充性**，然後**VSIX 專案**。)將方案命名為 `ViewPropertyTest`。  
  
2.  將編輯器分類器項目範本加入專案。 如需詳細資訊，請參閱 <<c0> [ 使用編輯器項目範本建立擴充](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  刪除現有類別檔案。  
  
## <a name="defining-the-content-type"></a>定義內容類型  
  
1. 加入類別檔案，並將它命名為 `ViewPropertyModifier`。  
  
2. 新增下列`using`指示詞：  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#1)]
    [!code-vb[VSSDKViewPropertyTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#1)]  
  
3. 宣告類別，名為`TestViewCreationListener`繼承自<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>。 匯出這個類別具有下列屬性：  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 若要指定要套用此接聽程式的內容類型。  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> 若要指定此接聽程式的角色。  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#2)]
     [!code-vb[VSSDKViewPropertyTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#2)]  
  
4. 在此類別中，匯入<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>。  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#3)]
    [!code-vb[VSSDKViewPropertyTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#3)]  
  
## <a name="changing-the-view-properties"></a>變更檢視的屬性  
  
1.  實作<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>方法以便開啟檢視時，會變更檢視的屬性。 若要進行變更，請先找到<xref:System.Windows.ResourceDictionary>，其對應於您想要尋找的檢視的外觀。 然後變更資源字典中適當的屬性，並設定屬性。 若要呼叫的批次<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>藉由呼叫的方法<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A>方法之前設定的屬性，然後<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A>設定屬性之後。  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#4)]
     [!code-vb[VSSDKViewPropertyTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#4)]  
  
## <a name="building-and-testing-the-code"></a>建置和測試程式碼  
  
1.  建置方案。  
  
     當您在偵錯工具中執行這個專案時，會具現化第二個 Visual Studio 執行個體。  
  
2.  建立文字檔，並輸入一些文字。  
  
    -   插入號應該是洋紅，覆寫插入號應該是淺粉藍  
  
    -   指示區邊界 （以 [文字] 檢視的左邊） 應指示燈綠色。  
  
3.  選取您剛才輸入的文字。 選取的文字的色彩應指示燈粉紅色。  
  
4.  選取文字時，請按一下 [文字] 視窗外的任何位置。 選取的文字的色彩應該深粉紅。  
  
5.  開啟可見的空白字元。 (在**編輯**功能表上，指向**進階**，然後按一下 **檢視空白區**)。 輸入文字中的某些索引標籤。 應該會顯示紅色的箭頭，表示索引標籤。  
  
## <a name="see-also"></a>另請參閱  
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)

