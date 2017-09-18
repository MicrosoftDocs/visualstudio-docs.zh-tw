---
title: "逐步解說: 將內容類型連結至檔案名稱副檔名 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，新的連結內容類型為檔案副檔名"
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# 逐步解說: 將內容類型連結至檔案名稱副檔名
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以定義您自己的內容類型，並使用編輯器 Managed Extensibility Framework \(MEF\) 延伸模組，將副檔名連結到它。 在某些情況下，檔案的副檔名已經定義的語言服務。不過，使用 MEF 您仍必須將它連結到內容類型。  
  
## 必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 建立 MEF 專案  
  
1.  建立 C\# VSIX 專案。 \(在 **新的專案** 對話方塊中，選取 **Visual C\# \/ 擴充性**, ，然後 **VSIX 專案**。\) 將方案命名為 `ContentTypeTest`。  
  
2.  在 **source.extension.vsixmanifest** 檔案，請移至 **資產** 索引標籤，然後設定 **類型** 欄位 **Microsoft.VisualStudio.MefComponent**, 、 **來源** 欄位 **目前方案中的專案**, ，和 **專案** 欄位設為專案的名稱。  
  
## 定義內容類型  
  
1.  將類別檔案，並將它 `FileAndContentTypes`。  
  
2.  加入下列組件的參考：  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  新增下列 `using` 指示詞。  
  
    ```c#  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  宣告靜態類別中包含的定義。  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  在此類別中匯出 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> 名為 「 隱藏 」 和 「 文字 」，為其基底定義宣告。  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## 內容類型連結的檔案名稱副檔名  
  
-   若要將此內容類型對應至檔案的副檔名，匯出 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> 擴充功能的 「.hid 」 和內容類型 「 隱藏 」。  
  
    ```c#  
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
  
## 將內容類型加入至編輯器匯出  
  
1.  建立編輯器延伸模組。 例如，您可以使用邊界圖像 \(glyph\) 延伸模組中所述 [逐步解說︰ 建立邊界圖像](../extensibility/walkthrough-creating-a-margin-glyph.md)。  
  
2.  加入您在此程序中定義的類別。  
  
3.  當您匯出的擴充類別時，加入 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 「 隱藏 」 給它的型別。  
  
    ```c#  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## 請參閱  
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)