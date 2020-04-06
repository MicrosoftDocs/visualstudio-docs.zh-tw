---
title: 演練:將內容類型連結到檔案名副檔名 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 328be013b5d522938cd7450fc53d4866c632abb3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697072"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>演練:將內容類型連結到檔案名副檔名
您可以使用編輯器託管擴展框架 (MEF) 延伸名定義自己的內容類型並將檔案名擴展名連結到該副檔名。 在某些情況下,檔名擴展名已由語言服務定義。 但是,要將其與 MEF 一起使用,您仍必須將其連結到內容類型。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-mef-project"></a>建立 MEF 專案

1. 創建 C# VSIX 專案。 ( 在 **'新增項目'** 對話框中,選擇**視覺化 C# / 可擴充性**,然後選擇**VSIX 專案**。命名解決方案`ContentTypeTest`。

2. 在**source.延伸.vsixmanifest 檔案中**,轉到 **「資產**」選項卡,並將 **「類型」** 欄位設定為**Microsoft.VisualStudio.Mef 元件**,**將「源**」欄位設定為**目前解決方案中的專案**,並將**專案**欄位設定為專案名稱。

## <a name="define-the-content-type"></a>定義內容類型

1. 加入類別檔案，並將它命名為 `FileAndContentTypes`。

2. 加入下列組件的參考：

    1. System.ComponentModel.Composition

    2. 微軟.VisualStudio.文本.邏輯

    3. 微軟.VisualStudio.核心實用程式

3. 添加以下`using`指令。

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Utilities;

    ```

4. 聲明包含定義的靜態類。

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {. . .}
    ```

5. 在此類中,匯出名為<xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>「隱藏」並將其基本定義聲明為"文本"。

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
        [Export]
        [Name("hid")]
        [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;
    }
    ```

## <a name="link-a-file-name-extension-to-a-content-type"></a>將檔案名副檔名連結到內容類型

- 要將此內容類型映射到檔案名副檔名,匯出<xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>具有 副檔名 *.hid*和內容類型"hid" 的 。

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

## <a name="add-the-content-type-to-an-editor-export"></a>將內容型別加入編輯器匯出

1. 建立編輯器擴展。 例如,您可以使用演練中描述的邊距字形擴展[:建立邊距字形](../extensibility/walkthrough-creating-a-margin-glyph.md)。

2. 添加在此過程中定義的類。

3. 匯出擴充類時,向其添加<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>類型 為"隱藏"。

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>另請參閱
- [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
