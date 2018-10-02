---
title: 結構的 [Content_types].xml 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 89c5e1bab9f8cbe8cd6e2b980013c6bfdf4bc039
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500008"
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>結構的 [Content_types].xml 檔案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[的 [Content_types].xml 檔案的結構](https://docs.microsoft.com/visualstudio/extensibility/the-structure-of-the-content-types-dot-xml-file)。  
  
包含在 VSIX 封裝的內容類型的相關資訊。 Visual Studio 安裝套件，請使用 [Content_Types].xml 檔案，但它不會安裝檔案本身。  
  
> [!NOTE]
>  雖然本主題只適用於 VSIX 封裝中所使用的 [有效].xml 檔案，但是 [Content_Types].xml 檔案類型會是一部分*開放封裝慣例 (OPC)* 標準。 如需詳細資訊，請參閱 < [OPC: 新標準的封裝資料](http://go.microsoft.com/fwlink/?LinkID=148207)MSDN 網站上。  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述的根項目和其屬性和子項目。  
  
### <a name="root-element"></a>根項目  
  
|元素|描述|  
|-------------|-----------------|  
|`Types`|包含列舉 VSIX 封裝中的檔案類型的子項目。|  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`Xmlns`|(必要項。)用於此 [Content_Types].xml 檔案的結構描述的位置。|  
  
### <a name="attribute-name-attribute"></a>{屬性 name}屬性  
  
|值|描述|  
|-----------|-----------------|  
|http://schemas.openformats.org/package/2006/content-types|內容類型的結構描述的位置。|  
  
### <a name="child-elements"></a>子元素  
 `Types`項目可以包含任意數目的`Default`項目。  
  
|元素|描述|  
|-------------|-----------------|  
|`Default`|描述 VSIX 封裝中的內容類型。 在封裝中的每個檔案類型必須有它自己`Default`項目。|  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`Extension`|VSIX 套件中之檔案的副檔名。|  
|`ContentType`|描述檔案名稱的副檔名相關聯的內容的類型。|  
  
### <a name="attribute-name-attribute"></a>{屬性 name}屬性  
 Visual Studio 可以辨識下列`ContentType`相關聯的值`Extension`型別。  
  
|副檔名|ContentType|  
|---------------|-----------------|  
|txt|text/plain|  
|pkgdef|text/plain|  
|xml|text/xml|  
|vsixmanifest|text/xml|  
|htm 或 html|text/html|  
|rtf|應用程式 /rtf|  
|pdf|應用程式/pdf|  
|gif|image/gif|  
|jpg 或 jpeg|映像/jpg|  
|Tiff|tiff 影像 /|  
|vsix|應用程式/郵遞區號|  
|zip|應用程式/郵遞區號|  
|dll|application/octet-stream|  
|所有其他檔案類型|application/octet-stream|  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列的 [Content_Types].xml 檔案會說明一般的 VSIX 套件。  
  
### <a name="code"></a>程式碼  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
    <Default Extension="vsixmanifest" ContentType="text/xml" />   
    <Default Extension="dll" ContentType="application/octet-stream" />   
    <Default Extension="png" ContentType="application/octet-stream" />   
    <Default Extension="txt" ContentType="text/plain" />   
    <Default Extension="pkgdef" ContentType="text/plain" />   
</Types>  
```  
  
## <a name="see-also"></a>另請參閱  
 [VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX 延伸結構描述 1.0 參考](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC： 新的標準封裝資料](http://go.microsoft.com/fwlink/?LinkID=148207)

