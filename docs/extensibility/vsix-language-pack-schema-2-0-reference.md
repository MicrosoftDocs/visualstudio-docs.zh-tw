---
title: VSIX 語言套件架構2.0 參考 |Microsoft Docs
description: VSIX 語言套件架構會提供 VSIX 封裝的當地語系化安裝資訊。 版本2.0 支援其他當地語系化元素。
ms.custom: SEO-VS-2020
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
author: acangialosi
ms.author: anthc
manager: jillfra
ms.openlocfilehash: fc9c3c1aa7f8cf77ebf165a3e10a67ccbd5887f7
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863820"
---
# <a name="vsix-language-pack-schema-20-reference"></a>VSIX 語言套件架構2.0 參考

VSIX 語言套件架構會提供 VSIX 封裝的當地語系化安裝資訊。 此架構的版本2.0 支援其他當地語系化元素。

## <a name="language-pack-schema"></a>語言套件架構

語言套件檔案的根項目是 `<PackageLanguagePackManifest>` ，具有的屬性 `Version` ，也就是語言套件格式的版本。 本文描述語言套件格式的版本2.0，該格式是藉由將屬性設定為值，在資訊清單中指定 `Version` `Version="2.0.0"` 。 根項目只包含一個子 `<Metadata>` 元素。

### <a name="packagelanguagepackmanifest-element"></a>PackageLanguagePackManifest 元素

在 `<PackageLanguagePackManifest>` 元素中，下列元素必須存在：

|標題|描述|
|-----------|-----------------|
|`<Metadata>`| 所有當地語系化套件中繼資料的包含元素

### <a name="metadata-element"></a>Metadata 元素

在 `<Metadata>` 元素中，您可以具有下列元素：

|標題|描述|
|-----------|-----------------|
|`<DisplayName>`|要安裝之延伸模組的當地語系化名稱|
|`<Description>`|要安裝之延伸模組的當地語系化描述|
|`<License>`| 延伸模組授權之當地語系化版本的路徑|
|`<MoreInfo>`| 有關延伸模組之當地語系化資訊的連結|
|`<ReleaseNotes>`| 版本資訊之當地語系化版本的路徑或連結|
|`<Icon>`| 當地語系化版本的延伸模組圖示路徑|

### <a name="sample-manifest"></a>資訊清單範例

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>請參閱

|標題|描述|
|-----------|-----------------|
|[將 VSIX 封裝當地語系化](../extensibility/localizing-vsix-packages.md)|示範如何針對 VSIX 套件提供當地語系化的安裝支援。|
|[VSIX 延伸架構2.0 參考](../extensibility/vsix-extension-schema-2-0-reference.md)|VSIX 資訊清單會描述 *.vsix* 部署檔案的內容。 部署檔案可讓您使用 [ **擴充功能和更新** ] 對話方塊來安裝 Visual Studio 擴充功能。|
|[尋找和使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)|示範如何使用 [ **擴充功能和更新** ] 對話方塊來安裝、移除、啟用和停用擴充功能。|
