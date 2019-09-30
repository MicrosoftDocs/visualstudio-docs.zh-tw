---
title: VSIX 語言套件架構2.0 參考 |Microsoft Docs
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
ms.author: zorio
author: zoeyr
manager: jillfra
ms.openlocfilehash: fe6d4bd9e82950d77925dda1560b5c204633d392
ms.sourcegitcommit: dae5dfd626277b58ebd7b21a75757f683f1eacc5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739336"
---
# <a name="vsix-language-pack-schema-20-reference"></a>VSIX 語言套件架構2.0 參考

VSIX 語言套件架構提供 VSIX 封裝的當地語系化安裝資訊。 此架構的2.0 版支援其他當地語系化元素。

## <a name="language-pack-schema"></a>語言套件架構

語言套件檔案的根項目是`<PackageLanguagePackManifest>`，具有的`Version`屬性，也就是語言套件格式的版本。 本文描述語言套件格式的版本2.0，其會將`Version`屬性設定為值`Version="2.0.0"`，以在資訊清單中指定。 根項目只包含一個子`<Metadata>`元素。

### <a name="packagelanguagepackmanifest-element"></a>PackageLanguagePackManifest 元素

`<PackageLanguagePackManifest>`在元素中，下列元素必須存在：

|標題|描述|
|-----------|-----------------|
|`<Metadata>`| 所有當地語系化套件中繼資料的包含元素

### <a name="metadata-element"></a>Metadata 元素

`<Metadata>`在元素內，您可以具有下列元素：

|標題|描述|
|-----------|-----------------|
|`<DisplayName>`|要安裝之延伸模組的當地語系化名稱|
|`<Description>`|要安裝之延伸模組的當地語系化描述|
|`<License>`| 延伸模組授權的當地語系化版本路徑|
|`<MoreInfo>`| 有關延伸模組的當地語系化資訊連結|
|`<ReleaseNotes>`| 版本資訊的當地語系化版本路徑或連結|
|`<Icon>`| 延伸模組圖示的當地語系化版本路徑|

### <a name="sample-manifest"></a>範例資訊清單

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</LocalizedName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>另請參閱

|標題|說明|
|-----------|-----------------|
|[當地語系化 VSIX 封裝](../extensibility/localizing-vsix-packages.md)|示範如何為 VSIX 封裝提供當地語系化的安裝支援。|
|[VSIX 延伸模組架構2.0 參考](../extensibility/vsix-extension-schema-2-0-reference.md)|VSIX 資訊清單會描述 *.vsix*部署檔案的內容。 部署檔案可讓您使用 [**擴充功能和更新**] 對話方塊來安裝 Visual Studio 延伸模組。|
|[尋找和使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)|示範如何使用 [**擴充功能和更新**] 對話方塊來安裝、移除、啟用和停用延伸模組。|
