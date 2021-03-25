---
title: 將內容類型連結至副檔名
description: 瞭解如何在此逐步解說中使用編輯器 Managed Extensibility Framework 延伸模組，將您自己的內容類型連結至副檔名。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 990f10fe82b9230c12ba13d736750f2f644c3ee5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078444"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>逐步解說：將內容類型連結至副檔名
您可以定義自己的內容類型，並使用編輯器 Managed Extensibility Framework (MEF) 擴充功能來連結副檔名。 在某些情況下，副檔名已由語言服務定義。 但是，若要搭配 MEF 使用它，您仍然必須將它連結至內容類型。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-mef-project"></a>建立 MEF 專案

1. 建立 c # VSIX 專案。  (在 [ **新增專案** ] 對話方塊中，選取 [ **Visual c #/** 擴充性]，然後選取 [ **VSIX 專案**]。 ) 為方案命名 `ContentTypeTest` 。

2. 在 **extension.vsixmanifest** 檔案中，移至 [ **資產** ] 索引標籤，並將 [ **類型** ] 欄位設定為 [ **VisualStudio**]、[ **來源** ] 欄位設定為 [ **目前方案中的專案**]，並將 [ **專案** ] 欄位設定為專案的名稱。

## <a name="define-the-content-type"></a>定義內容類型

1. 加入類別檔案，並將它命名為 `FileAndContentTypes`。

2. 加入下列組件的參考：

    1. System.ComponentModel.Composition

    2. VisualStudio。

    3. VisualStudio. CoreUtility

3. 新增下列指示詞 `using` 。

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Utilities;

    ```

4. 宣告包含定義的靜態類別。

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {. . .}
    ```

5. 在這個類別中，匯出 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> 名為 "hid" 的，並將其基底定義宣告為 "text"。

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
        [Export]
        [Name("hid")]
        [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;
    }
    ```

## <a name="link-a-file-name-extension-to-a-content-type"></a>將副檔名連結至內容類型

- 若要將這個內容類型對應至副檔名，請匯出副檔名為的， <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> 且內容類型為 "hid" 的。

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
         [Export]
         [Name("hid")]
         [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;

         [Export]
         [FileExtension(".hid")]
         [ContentType("hid")]
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;
    }
    ```

## <a name="add-the-content-type-to-an-editor-export"></a>將內容類型新增至編輯器匯出

1. 建立編輯器延伸模組。 例如，您可以使用 [ [逐步解說：建立邊界](../extensibility/walkthrough-creating-a-margin-glyph.md)字元] 中所述的邊界字元延伸。

2. 新增您在此程式中定義的類別。

3. 當您匯出擴充類別時，請在 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 其中加入 "hid" 類型。

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>另請參閱
- [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
