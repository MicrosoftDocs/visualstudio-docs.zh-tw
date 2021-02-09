---
title: '[Content_types] .xml 檔案的結構 |Microsoft Docs'
description: 深入瞭解內容類型檔案的結構，其中包含 VSIX 封裝中內容類型的相關資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 38348661946be3894332d49177f972410563b716
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895203"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>[Content_types].xml 檔案的結構
包含 VSIX 封裝中內容類型的相關資訊。 Visual Studio 使用 [Content_Types] .xml 檔案安裝套件，但不會安裝檔案本身。

> [!NOTE]
> 雖然本主題僅適用于 VSIX 封裝中所使用的 [Content_Type] .xml 檔案，但 [Content_Types] .xml 檔案類型是 *開放式封裝慣例 (OPC)* 標準的一部分。 如需詳細資訊，請參閱 [OPC：將資料封裝](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data) 在 MSDN 網站的新標準。

## <a name="attributes-and-elements"></a>屬性和項目
 下列各節描述根項目及其屬性和子項目。

### <a name="root-element"></a>根項目

|元素|描述|
|-------------|-----------------|
|`Types`|包含列舉 VSIX 封裝中檔案類型的子項目。|

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Xmlns`| (必要項。 ) 用於這個 [Content_Types] .xml 檔案的架構位置。|

### <a name="attribute-name-attribute"></a>{屬性名稱}屬性

| 值 | 描述 |
| - | - |
| `http://schemas.openformats.org/package/2006/content-types` | 內容類型架構的位置。 |

### <a name="child-elements"></a>子元素
 `Types` 元素可以包含不限數目的 `Default` 元素。

|元素|描述|
|-------------|-----------------|
|`Default`|描述 VSIX 套件中的內容類型。 封裝中的每個檔案類型都必須有自己的 `Default` 元素。|

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Extension`|VSIX 封裝中檔案的副檔名。|
|`ContentType`|描述與副檔名相關聯的內容類型。|

### <a name="attribute-name-attribute"></a>{屬性名稱}屬性
 Visual Studio 可辨識 `ContentType` 相關聯類型的下列值 `Extension` 。

|分機|ContentType|
|---------------|-----------------|
|txt|text/plain|
|.pkgdef|text/plain|
|Xml|text/xml|
|extension.vsixmanifest|text/xml|
|htm 或 html|text/html|
|Rtf|應用程式/rtf|
|pdf|應用程式/pdf|
|GIF|image/gif|
|jpg 或 jpeg|影像/jpg|
|tiff|image/tiff|
|vsix|應用程式/zip|
|zip|應用程式/zip|
|dll|application/octet-stream|
|所有其他檔案類型|application/octet-stream|

## <a name="example"></a>範例

### <a name="description"></a>描述
 下列 [Content_Types] .xml 檔案描述一般 VSIX 套件。

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
- [VSIX 延伸架構1.0 參考](/previous-versions/dd393700(v=vs.110))
- [OPC：封裝資料的新標準](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data)