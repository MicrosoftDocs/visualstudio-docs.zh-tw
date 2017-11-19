---
title: "逐步解說： 自訂文字檢視 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e890145199fe864d2f7b5010495375bfbc6cc094
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-customizing-the-text-view"></a>逐步解說： 自訂文字檢視
您可以自訂文字檢視藉由修改任何其編輯器格式對應中的下列屬性：  
  
-   指示區邊界  
  
-   插入插入號  
  
-   覆寫插入號  
  
-   選取的文字  
  
-   非現用選取的文字 （也就是選取的文字已遺失焦點）  
  
-   顯示空白字元  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>建立 MEF 專案  
  
1.  建立 C# VSIX 專案。 (在**新專案**對話方塊中，選取**Visual C# / 擴充性**，然後**VSIX 專案**。)將方案命名`ViewPropertyTest`。  
  
2.  編輯器分類器項目範本加入專案。 如需詳細資訊，請參閱[編輯器項目範本以建立擴充](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  刪除現有類別檔案。  
  
## <a name="defining-the-content-type"></a>定義的內容類型  
  
1.  將類別檔案並將其命名`ViewPropertyModifier`。  
  
2.  加入下列`using`指示詞：  
  
     [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
     [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3.  宣告類別，名為`TestViewCreationListener`繼承自<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>。 匯出類別具有下列屬性：  
  
    -   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>若要指定要套用此接聽程式的內容類型。  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>若要指定此接聽程式的角色。  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4.  這個類別，在匯入<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>。  
  
     [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
     [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="changing-the-view-properties"></a>變更檢視屬性  
  
1.  實作<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>方法以便開啟檢視時，會變更檢視內容。 若要進行變更，請先找出<xref:System.Windows.ResourceDictionary>對應於您想要尋找的檢視的外觀。 然後變更 資源字典中適當的屬性和設定的屬性。 若要呼叫的批次<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>方法藉由呼叫<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A>方法之前設定的屬性，然後<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A>設定屬性之後。  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="building-and-testing-the-code"></a>建置和測試程式碼  
  
1.  建置方案。  
  
     當您在偵錯工具中執行這個專案時，會具現化第二個 Visual Studio 執行個體。  
  
2.  建立文字檔，並輸入一些文字。  
  
    -   插入號應該洋紅及覆寫插入號應該淺粉藍色陰影。  
  
    -   指示區邊界 （以 [文字] 檢視的左邊） 應該是淺綠色。  
  
3.  選取您剛才輸入的文字。 所選取文字的色彩應該是淺色粉紅色。  
  
4.  選取文字時，按一下文字時段以外的任何位置。 所選取文字的色彩應該是深色粉紅色。  
  
5.  開啟可見的空白字元。 (在**編輯**功能表上，指向**進階**，然後按一下 **檢視空白區**)。 某些索引標籤中輸入的文字。 應該會顯示紅色的箭頭表示索引標籤。  
  
## <a name="see-also"></a>另請參閱  
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)