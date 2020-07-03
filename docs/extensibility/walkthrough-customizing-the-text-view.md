---
title: 逐步解說：自訂文字視圖 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b7a62ee2b55bf2b56ae1d8e28fc1910ed444c29
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904937"
---
# <a name="walkthrough-customize-the-text-view"></a>逐步解說：自訂文字視圖
您可以在其編輯器格式對應中修改下列任何屬性，以自訂文字視圖：

- 指示區邊界

- 插入插入號

- 覆寫插入號

- 選取的文字

- 非使用中的選取文字（也就是遺失焦點的已選取文字）

- 可見的空白字元

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選擇性功能。 您稍後也可以安裝 VS SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-mef-project"></a>建立 MEF 專案

1. 建立 c # VSIX 專案。 （在 [**新增專案**] 對話方塊中，選取 [ **Visual c #/** 擴充性]、[ **VSIX 專案**]）。將方案命名為 `ViewPropertyTest` 。

2. 將編輯器分類器專案範本加入至專案。 如需詳細資訊，請參閱[使用編輯器專案範本建立擴充](../extensibility/creating-an-extension-with-an-editor-item-template.md)功能。

3. 刪除現有類別檔案。

## <a name="define-the-content-type"></a>定義內容類型

1. 加入類別檔案，並將它命名為 `ViewPropertyModifier`。

2. 新增下列 `using` 指示詞：

    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]

3. 宣告 `TestViewCreationListener` 繼承自的類別，名為 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> 。 使用下列屬性匯出此類別：

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>指定此接聽程式所套用的內容類型。

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>指定此接聽程式的角色。

     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]

4. 在此類別中，匯入 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> 。

    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]

## <a name="change-the-view-properties"></a>變更視圖屬性

1. 設定方法， <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> 以便在開啟此視圖時變更視圖屬性。 若要進行變更，請先找出 <xref:System.Windows.ResourceDictionary> 對應至您要尋找之視圖層面的。 然後，在資源字典中變更適當的屬性，並設定屬性。 藉由呼叫方法來批次處理方法的呼叫，然後在 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> 設定屬性之後，設定 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> 屬性之後。

     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]

## <a name="build-and-test-the-code"></a>建立並測試程式碼

1. 建置方案。

     當您在偵錯工具中執行此專案時，會啟動 Visual Studio 的第二個實例。

2. 建立文字檔，並輸入一些文字。

    - 插入插入號應該是洋紅，而覆寫插入號應該是藍綠色。

    - 指標邊界（位於文字視圖的左邊）應該是淺綠色。

3. 選取您輸入的文字。 選取文字的色彩應該是淺粉色。

4. 選取文字時，請按一下文字視窗外的任何位置。 選取文字的色彩應該是暗粉紅色。

5. 開啟可見的空白字元。 （在 [**編輯**] 功能表上，指向 [ **Advanced** ]，然後按一下 [ **View 空白字元**]）。 在文字中輸入一些索引標籤。 應該會顯示代表索引標籤的紅色箭號。

## <a name="see-also"></a>另請參閱
- [語言服務和編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
