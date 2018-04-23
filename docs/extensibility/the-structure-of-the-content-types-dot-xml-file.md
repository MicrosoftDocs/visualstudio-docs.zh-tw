---
title: '[Content_types].xml 檔案的結構 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 38e65f484411abcfb2acd78b124b77ff3f2c49cd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>[Content_types].xml 檔案的結構
包含在 VSIX 封裝的內容類型的相關資訊。 Visual Studio 會使用 [Content_Types].xml 檔案來安裝封裝，但不會安裝該檔案本身。  
  
> [!NOTE]
>  雖然本主題只適用於使用 VSIX 封裝中的 [有效].xml 檔案，但是 [Content_Types].xml 檔案類型屬於的*開放封裝慣例 (OPC)*標準。 如需詳細資訊，請參閱[OPC: 新標準為封裝資料](http://go.microsoft.com/fwlink/?LinkID=148207)MSDN 網站上。  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述的根項目與屬性和子項目。  
  
### <a name="root-element"></a>根項目  
  
|項目|描述|  
|-------------|-----------------|  
|`Types`|包含列舉 VSIX 封裝中的檔案類型的子項目。|  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`Xmlns`|(必要項。)使用此 [Content_Types].xml 檔案的結構描述位置。|  
  
### <a name="attribute-name-attribute"></a>{屬性名稱}屬性  
  
|值|描述|  
|-----------|-----------------|  
|http://schemas.openformats.org/package/2006/content-types|內容類型結構描述的位置。|  
  
### <a name="child-elements"></a>子項目  
 `Types`項目可以包含任意數目的`Default`項目。  
  
|項目|描述|  
|-------------|-----------------|  
|`Default`|描述 VSIX 封裝中的內容型別。 每個封裝中的檔案類型必須有它自己`Default`項目。|  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`Extension`|VSIX 套件中之檔案的副檔名。|  
|`ContentType`|描述檔案名稱的副檔名相關聯的內容的類型。|  
  
### <a name="attribute-name-attribute"></a>{屬性名稱}屬性  
 Visual Studio 可辨識下列`ContentType`值相關聯之`Extension`型別。  
  
|副檔名|ContentType|  
|---------------|-----------------|  
|txt|文字/純文字|  
|pkgdef|文字/純文字|  
|xml|text/xml|  
|vsixmanifest|text/xml|  
|htm 或 html|text/html|  
|rtf|應用程式/rtf|  
|pdf|應用程式/pdf|  
|gif|gif 影像|  
|jpg 或 jpeg|jpg 影像 /|  
|Tiff|tiff 影像 /|  
|vsix|應用程式/郵遞區號|  
|郵遞區號|應用程式/郵遞區號|  
|dll|application/octet-stream|  
|所有其他檔案類型|application/octet-stream|  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列 [Content_Types].xml 檔案會描述一般的 VSIX 封裝。  
  
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
 [VSIX 擴充功能的結構描述 1.0 參考](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC： 新的標準來包裝您的資料](http://go.microsoft.com/fwlink/?LinkID=148207)