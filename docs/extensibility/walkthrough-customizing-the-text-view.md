---
title: 逐步解說：自訂文字檢視 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a697456a15008f305b92aacfb1485be1c08c062
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54920393"
---
# <a name="walkthrough-customize-the-text-view"></a>逐步解說：自訂文字檢視
您可以自訂文字檢視，方法是修改任何它的編輯器格式對應中的下列屬性：  
  
-   指示區邊界  
  
-   插入號  
  
-   覆寫插入號  
  
-   選取的文字  
  
-   非現用選取的文字 （也就是選取的文字已遺失焦點）  
  
-   可見的空白字元  
  
## <a name="prerequisites"></a>必要條件  
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 它包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="create-a-mef-project"></a>建立 MEF 專案  
  
1.  建立 C# VSIX 專案。 (在**新的專案**對話方塊中，選取**Visual C# / 擴充性**，然後**VSIX 專案**。)將方案命名為 `ViewPropertyTest`。  
  
2.  將編輯器分類器項目範本加入專案。 如需詳細資訊，請參閱 <<c0> [ 使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  刪除現有類別檔案。  
  
## <a name="define-the-content-type"></a>內容類型定義  
  
1. 加入類別檔案，並將它命名為 `ViewPropertyModifier`。  
  
2. 新增下列`using`指示詞：  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3. 宣告類別，名為`TestViewCreationListener`繼承自<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>。 匯出這個類別具有下列屬性：  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 若要指定要套用此接聽程式的內容類型。  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> 若要指定此接聽程式的角色。  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4. 在此類別中，匯入<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>。  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="change-the-view-properties"></a>變更檢視的屬性  
  
1.  設定<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>方法以便開啟檢視時，會變更檢視的屬性。 若要進行變更，請先找到<xref:System.Windows.ResourceDictionary>，其對應於您想要尋找的檢視的外觀。 然後，變更資源字典中適當的屬性，並設定屬性。 若要呼叫的批次<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>藉由呼叫的方法<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A>方法之前設定的屬性，然後<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A>設定屬性之後。  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="build-and-test-the-code"></a>建置和測試程式碼  
  
1.  建置方案。  
  
     當您執行此專案的偵錯工具時，會啟動 Visual Studio 的第二個執行個體。  
  
2.  建立文字檔，並輸入一些文字。  
  
    -   插入號應該是洋紅，覆寫插入號應該是淺粉藍  
  
    -   指示區邊界 （以 [文字] 檢視的左邊） 應指示燈綠色。  
  
3.  選取您所輸入的文字。 選取的文字的色彩應指示燈粉紅色。  
  
4.  選取文字時，請按一下 [文字] 視窗外的任何位置。 選取的文字的色彩應該深粉紅。  
  
5.  開啟可見的空白字元。 (在**編輯**功能表上，指向**進階**，然後按一下 **檢視空白區**)。 輸入文字中的某些索引標籤。 應該會顯示紅色的箭頭，表示索引標籤。  
  
## <a name="see-also"></a>另請參閱  
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)