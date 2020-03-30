---
title: '[Content_types]xml 檔的結構 |微軟文檔'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 957958cd930620734d09c592ea07bfb0919d0145
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395309"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>[Content_types].xml 檔案的結構
包含有關 VSIX 包中內容類型的資訊。 Visual Studio 使用 [Content_Types]xml 檔來安裝包，但它不會自行安裝該檔。

> [!NOTE]
> 儘管本主題僅適用于 VSIX 包中使用的 [Content_Type]xml 檔，但 [Content_Types]xml 檔案類型是*開放打包約定 （OPC）* 標準的一部分。 有關詳細資訊，請參閱 OPC：在 MSDN 網站上[打包資料的新標準](https://msdn.microsoft.com/magazine/cc163372.aspx)。

## <a name="attributes-and-elements"></a>屬性和項目
 以下各節介紹根項目及其屬性和子項目。

### <a name="root-element"></a>根項目

|元素|描述|
|-------------|-----------------|
|`Types`|包含枚舉 VSIX 包中的檔案類型的子項目。|

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Xmlns`|（必需。用於此 [Content_Types]xml 檔的架構的位置。|

### <a name="attribute-name-attribute"></a>[屬性名稱]屬性

| 值 | 描述 |
| - | - |
| `http://schemas.openformats.org/package/2006/content-types` | 內容類型架構的位置。 |

### <a name="child-elements"></a>子元素
 `Types` 元素可以包含不限數目的 `Default` 元素。

|元素|描述|
|-------------|-----------------|
|`Default`|描述 VSIX 包中的內容類型。 包中的每個檔案類型都必須有自己的`Default`元素。|

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Extension`|VSIX 包中檔的檔案名副檔名。|
|`ContentType`|描述與檔案名副檔名關聯的內容類型。|

### <a name="attribute-name-attribute"></a>[屬性名稱]屬性
 Visual Studio 可識別關聯`ContentType``Extension`類型的以下值。

|分機|ContentType|
|---------------|-----------------|
|txt|text/plain|
|普格德夫|text/plain|
|Xml|text/xml|
|vsixmanifest|text/xml|
|htm 或 html|text/html|
|Rtf|應用程式/rtf|
|pdf|應用程式/pdf|
|GIF|image/gif|
|jpg 或 jpeg|圖像/jpg|
|tiff|image/tiff|
|vsix|應用程式/zip|
|zip|應用程式/zip|
|dll|application/octet-stream|
|所有其他檔案類型|application/octet-stream|

## <a name="example"></a>範例

### <a name="description"></a>描述
 以下 [Content_Types]xml 檔描述了典型的 VSIX 包。

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
- [VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)
- [VSIX 擴展架構 1.0 參考](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [OPC：打包資料的新標準](https://msdn.microsoft.com/magazine/cc163372.aspx)