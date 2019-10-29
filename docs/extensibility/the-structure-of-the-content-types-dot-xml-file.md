---
title: '[Content_types] .xml 檔案的結構 |Microsoft Docs'
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
ms.openlocfilehash: aac250053f90d99e7db27a9862d2dc1b33fadbfb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983032"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>[Content_types].xml 檔案的結構
包含 VSIX 封裝中之內容類型的相關資訊。 Visual Studio 使用 [Content_Types] .xml 檔案來安裝封裝，但不會安裝檔案本身。

> [!NOTE]
> 雖然本主題僅適用于在 VSIX 封裝中使用的 [Content_Type] .xml 檔案，但 [Content_Types] .xml 檔案類型是*開放封裝慣例（OPC）* 標準的一部分。 如需詳細資訊，請參閱《 OPC：在 MSDN 網站上[封裝資料的新標準](https://msdn.microsoft.com/magazine/cc163372.aspx)\ （英文 \）。

## <a name="attributes-and-elements"></a>屬性和項目
 下列各節將描述根項目及其屬性和子項目。

### <a name="root-element"></a>根項目

|項目|描述|
|-------------|-----------------|
|`Types`|包含用來列舉 VSIX 封裝中之檔案類型的子項目。|

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Xmlns`|（必要）。這個 [Content_Types] .xml 檔案所使用之架構的位置。|

### <a name="attribute-name-attribute"></a>{屬性名稱}特性

| 值 | 描述 |
| - | - |
| http://schemas.openformats.org/package/2006/content-types | 內容類型架構的位置。 |

### <a name="child-elements"></a>子項目
 `Types` 元素可以包含任意數目的 `Default` 元素。

|項目|描述|
|-------------|-----------------|
|`Default`|描述 VSIX 封裝中的內容類型。 封裝中的每個檔案類型都必須有自己的 `Default` 元素。|

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Extension`|VSIX 封裝中檔案的副檔名。|
|`ContentType`|描述與副檔名相關聯的內容種類。|

### <a name="attribute-name-attribute"></a>{屬性名稱}特性
 Visual Studio 會辨識相關聯 `Extension` 類型的下列 `ContentType` 值。

|副檔名|contentType|
|---------------|-----------------|
|.txt|文字/純文字|
|.pkgdef|文字/純文字|
|xml|text/xml|
|extension.vsixmanifest|text/xml|
|htm 或 html|text/html|
|.rtf|應用程式/rtf|
|pdf|應用程式/pdf|
|gif|影像/gif|
|jpg 或 jpeg|影像/jpg|
|tiff|影像/tiff|
|vsix|應用程式/zip|
|zip|應用程式/zip|
|dll|application/octet-stream|
|所有其他檔案類型|application/octet-stream|

## <a name="example"></a>範例

### <a name="description"></a>描述
 下列 [Content_Types] .xml 檔案描述一般的 VSIX 封裝。

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

## <a name="see-also"></a>請參閱
- [VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)
- [VSIX 延伸模組架構1.0 參考](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [OPC：封裝資料的新標準](https://msdn.microsoft.com/magazine/cc163372.aspx)