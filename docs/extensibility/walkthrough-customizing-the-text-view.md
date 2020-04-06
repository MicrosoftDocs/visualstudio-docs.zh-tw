---
title: 演練:自定義文本視圖 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d99f9201761bbe079c34ccf61339158863509dd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697461"
---
# <a name="walkthrough-customize-the-text-view"></a>演練:自訂文字檢視
您可以透過修改編輯器格式映射中的以下任一屬性來自訂文字檢視:

- 指示區邊界

- 插入卡托

- 覆寫 care

- 選取的文字

- 非作用選取的文字(即失去焦點的選取的文字)

- 可見空白

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-mef-project"></a>建立 MEF 專案

1. 創建 C# VSIX 專案。 ( 在 **'新增項目'** 對話框中,選擇**視覺化 C# / 可擴充性**,然後選擇**VSIX 專案**。命名解決方案`ViewPropertyTest`。

2. 加入專案加入編輯器分類器項範本。 關於詳細資訊,請參考[使用編輯器項目樣本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3. 刪除現有類別檔案。

## <a name="define-the-content-type"></a>定義內容類型

1. 加入類別檔案，並將它命名為 `ViewPropertyModifier`。

2. 新增下列 `using` 指示詞：

    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]

3. 聲明從`TestViewCreationListener`繼承<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>的名為的類。 使用以下屬性匯出此類:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>指定此偵聽器應用的內容類型。

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>指定此偵聽器的角色。

     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]

4. 在此類中,匯入<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>。

    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]

## <a name="change-the-view-properties"></a>變更檢視屬性

1. 設置方法<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>,以便在打開檢視時更改視圖屬性。 要進行更改,首先查找<xref:System.Windows.ResourceDictionary>與要查找的視圖的方面對應的。 然後,更改資源字典中的相應屬性並設置屬性。 在設置屬性之前調用<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A><xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A>方法,然後在設置<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A>屬性 之後對 方法進行批處理調用。

     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]

## <a name="build-and-test-the-code"></a>組建及測試代碼

1. 建置方案。

     在除錯器中執行此專案時,將啟動 Visual Studio 的第二個實體。

2. 建立文字檔，並輸入一些文字。

    - 插入護記應該是洋紅色,覆蓋的護處理應該是綠松石。

    - 指標邊距(文字視圖左側)應為淺綠色。

3. 選取您輸入的文字。 所選文本的顏色應為淺粉紅色。

4. 選擇文字時,按一下文字視窗外部的任意位置。 所選文本的顏色應為深粉色。

5. 打開可見的空白。 (在 **"編輯"** 選單上,指向 **"高級",** 然後按一下「**查看空白**」 。。 在文字中鍵入某些選項卡。 應顯示表示選項卡的紅色箭頭。

## <a name="see-also"></a>另請參閱
- [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
