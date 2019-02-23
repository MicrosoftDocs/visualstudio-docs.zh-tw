---
title: 逐步解說：將內容類型連結至副檔名為 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e55c06ab5ae07c9b84f9d6462d1a535537e5f69b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56692836"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>逐步解說：將內容類型連結至副檔名
您可以定義您自己的內容類型，並連結到它的副檔名，透過使用編輯器的 Managed Extensibility Framework (MEF) 擴充功能。 在某些情況下，檔案名稱的副檔名已經定義的語言服務。 但是，若要使用它與 MEF，您必須仍將它連結至內容類型。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從下載中心取得。 它包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-mef-project"></a>建立 MEF 專案

1.  建立 C# VSIX 專案。 (在**新的專案**對話方塊中，選取**Visual C# / 擴充性**，然後**VSIX 專案**。)將方案命名為 `ContentTypeTest`。

2.  在  **source.extension.vsixmanifest**檔案中，移至**資產**索引標籤，然後將**型別**欄位設為**Microsoft.VisualStudio.MefComponent**，則**來源**欄位設為**目前方案中的專案**，而**專案**欄位設為專案的名稱。

## <a name="define-the-content-type"></a>內容類型定義

1.  加入類別檔案，並將它命名為 `FileAndContentTypes`。

2.  加入下列組件的參考：

    1.  System.ComponentModel.Composition

    2.  Microsoft.VisualStudio.Text.Logic

    3.  Microsoft.VisualStudio.CoreUtility

3.  新增下列`using`指示詞。

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Utilities;

    ```

4.  宣告靜態類別，包含定義。

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {. . .}
    ```

5.  在此類別中，匯出<xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>名為 「 隱藏 」，並宣告其基底定義為"text"。

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
        [Export]
        [Name("hid")]
        [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;
    }
    ```

## <a name="link-a-file-name-extension-to-a-content-type"></a>連結至內容類型的副檔名

-   若要將這個內容類型對應至檔案的副檔名，匯出<xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>具有延伸模組 *.hid*和內容類型 「 隱藏 」。

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

## <a name="add-the-content-type-to-an-editor-export"></a>將內容類型加入至編輯器匯出

1.  建立編輯器擴充功能。 例如，您可以使用邊界圖像 （glyph） 擴充功能中所述[逐步解說：建立邊界字符](../extensibility/walkthrough-creating-a-margin-glyph.md)。

2.  新增您在此程序中定義的類別。

3.  當您匯出延伸模組類別時，新增<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>「 隱藏 」 給它的型別。

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>另請參閱
- [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)