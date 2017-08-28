---
title: 'Walkthrough: Linking a Content Type to a File Name Extension | Microsoft Docs'
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
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 1bebe89c0bc2785f85bf38949ea477d2da662cc9
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>Walkthrough: Linking a Content Type to a File Name Extension
You can define your own content type and link a file name extension to it by using editor Managed Extensibility Framework (MEF) extensions. In some cases, the file name extension has already been defined by a language service; nevertheless, to use it with MEF you still must link it to a content type.  
  
## <a name="prerequisites"></a>Prerequisites  
 Starting in Visual Studio 2015, you do not install the Visual Studio SDK from the download center. It is included as an optional feature in Visual Studio setup. You can also install the VS SDK later on. For more information, see [Installing the Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creating a MEF Project  
  
1.  Create a C# VSIX project. (In the **New Project** dialog, select **Visual C# / Extensibility**, then **VSIX Project**.) Name the solution `ContentTypeTest`.  
  
2.  In the **source.extension.vsixmanifest** file, go to the **Assets** tab, and set the **Type** field to **Microsoft.VisualStudio.MefComponent**, the **Source** field to **A project in current solution**, and the **Project** field to the name of the project.  
  
## <a name="defining-the-content-type"></a>Defining the Content Type  
  
1.  Add a class file and name it `FileAndContentTypes`.  
  
2.  Add references to the following assemblies:  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  Add the following `using` directives.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  Declare a static class that contains the definitions.  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  In this class, export a <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> named "hid" and declare its base definition to be "text".  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>Linking a File Name Extension to a Content Type  
  
-   To map this content type to a file name extension, export a <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> that has the extension ".hid" and the content type "hid".  
  
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
  
## <a name="adding-the-content-type-to-an-editor-export"></a>Adding the Content Type to an Editor Export  
  
1.  Create an editor extension. For example, you can use the margin glyph extension described in [Walkthrough: Creating a Margin Glyph](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2.  Add the class you defined in this procedure.  
  
3.  When you export the extension class, add a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> of type "hid" to it.  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>See Also  
 [Language Service and Editor Extension Points](../extensibility/language-service-and-editor-extension-points.md)
