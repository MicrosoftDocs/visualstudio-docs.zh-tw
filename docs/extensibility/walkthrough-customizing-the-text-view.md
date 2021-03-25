---
title: 逐步解說：自訂文字視圖 |Microsoft Docs
description: 瞭解如何使用這個逐步解說，藉由在編輯器的格式對應中修改任何數個屬性，以自訂文字視圖。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 17aa8644fc4823df5b68378e9045fa190980306d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080303"
---
# <a name="walkthrough-customize-the-text-view"></a>逐步解說：自訂文字視圖
您可以在編輯器格式對應中修改下列任何屬性，以自訂文字視圖：

- 指示區邊界

- 插入插入號

- 覆寫插入號

- 選取的文字

- 非使用中的選取文字 (也就是選取的文字遺失焦點) 

- 可見空白

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-mef-project"></a>建立 MEF 專案

1. 建立 c # VSIX 專案。  (在 [ **新增專案** ] 對話方塊中，選取 [ **Visual c #/** 擴充性]，然後選取 [ **VSIX 專案**]。 ) 為方案命名 `ViewPropertyTest` 。

2. 將編輯器分類專案範本加入至專案。 如需詳細資訊，請參閱 [使用編輯器專案範本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3. 刪除現有類別檔案。

## <a name="define-the-content-type"></a>定義內容類型

1. 加入類別檔案，並將它命名為 `ViewPropertyModifier`。

2. 新增下列 `using` 指示詞：

    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]

3. 宣告名為 `TestViewCreationListener` 的類別，該類別繼承自 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> 。 使用下列屬性匯出此類別：

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 指定此接聽程式套用的內容類型。

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> 指定此接聽程式的角色。

     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]

4. 在這個類別中，匯入 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> 。

    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]

## <a name="change-the-view-properties"></a>變更視圖屬性

1. 設定方法， <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> 以便在開啟視圖時變更視圖屬性。 若要進行變更，請先找出 <xref:System.Windows.ResourceDictionary> 對應到您想要尋找之觀點的。 然後，在資源字典中變更適當的屬性，並設定屬性。 藉由呼叫方法來批次處理方法的呼叫，然後再 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> 設定屬性，然後在 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> 設定屬性之後設定。

     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]

## <a name="build-and-test-the-code"></a>建立並測試程式碼

1. 建置方案。

     當您在偵錯工具中執行此專案時，會啟動 Visual Studio 的第二個實例。

2. 建立文字檔，並輸入一些文字。

    - 插入插入號應該是洋紅色，覆寫插入號應該是青。

    - 文字視圖) 左邊的指標邊界 (應為淺綠色。

3. 選取您輸入的文字。 所選文字的色彩應該是淺粉紅色。

4. 選取文字時，請按一下文字視窗外的任何位置。 所選文字的色彩應該是深粉紅色。

5. 開啟可見的空白。  (在 [ **編輯** ] 功能表上，指向 [ **Advanced** ]，然後按一下 [ **View** 空白字元]) 。 在文字中輸入一些索引標籤。 應該會顯示代表索引標籤的紅色箭號。

## <a name="see-also"></a>另請參閱
- [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
