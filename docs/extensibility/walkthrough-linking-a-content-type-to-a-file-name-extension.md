---
title: "逐步解說： 將內容類型連結至檔案的副檔名 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5df3bab0a453f4f8edcff3be86e5a767065b59da
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>逐步解說： 將內容類型連結至檔案的副檔名
您可以定義您自己的內容類型，然後連結它透過使用編輯器 Managed Extensibility Framework (MEF) 擴充功能檔案的副檔名。 在某些情況下，檔案名稱的副檔名已經定義語言服務;不過，使用 MEF 您仍必須將它連結至內容類型。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>建立 MEF 專案  
  
1.  建立 C# VSIX 專案。 (在**新專案**對話方塊中，選取**Visual C# / 擴充性**，然後**VSIX 專案**。)將方案命名`ContentTypeTest`。  
  
2.  在**source.extension.vsixmanifest**檔案，請移至**資產**索引標籤，然後設定**類型**欄位設為**Microsoft.VisualStudio.MefComponent**、**來源**欄位設為**目前方案中的專案**，而**專案**欄位設為專案的名稱。  
  
## <a name="defining-the-content-type"></a>定義的內容類型  
  
1.  將類別檔案並將其命名`FileAndContentTypes`。  
  
2.  加入下列組件的參考：  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  加入下列`using`指示詞。  
  
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
  
5.  這個類別，在匯出<xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>名為 「 隱藏 」，並宣告其基底定義為 「 文字 」。  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>連結至內容類型的檔案名稱副檔名  
  
-   若要將此內容類型對應至檔案的副檔名，匯出<xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>，副檔名為".hid 」 和內容類型 「 隱藏 」。  
  
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
  
## <a name="adding-the-content-type-to-an-editor-export"></a>內容類型加入編輯器匯出  
  
1.  建立編輯器延伸模組。 例如，您可以使用邊界圖像 （glyph） 擴充功能中所述[逐步解說： 建立邊界圖像](../extensibility/walkthrough-creating-a-margin-glyph.md)。  
  
2.  加入您在此程序中定義的類別。  
  
3.  當您匯出延伸模組類別時，新增<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>「 隱藏 」 給它的型別。  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>請參閱  
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)