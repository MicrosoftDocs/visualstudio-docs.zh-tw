---
title: VSIX 語言套件結構描述 2.0 參考 |Microsoft Docs
ms.custom: ''
ms.date: 10/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
ms.author: dagriffe
author: dgriffen
manager: douge
ms.workload:
- dagriffe
ms.openlocfilehash: 94d785ce55b57e35b0880537e099cbc3e03d20ab
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855806"
---
# <a name="vsix-language-pack-schema-20-reference"></a>VSIX 語言套件結構描述 2.0 參考

VSIX 語言套件結構描述會提供 VSIX 封裝當地語系化的安裝資訊。 此結構描述的 2.0 版支援其他當地語系化的項目。

## <a name="language-pack-schema"></a>語言套件結構描述

語言組件檔案的根項目是`<PackageLanguagePackManifest>`，屬性為`Version`，這是語言組件格式的版本。 這篇文章描述的語言組件格式，藉由設定資訊清單中所指定的 2.0 版`Version`屬性的值`Version="2.0.0"`。 根項目包含一個子`<Metadata>`項目。

### <a name="packagelangaugepackmanifest-element"></a>PackageLangaugePackManifest 項目

內`<PackageLanguagePackManifest>`下列項目必須存在的項目：

|標題|描述|
|-----------|-----------------|
|`<Metadata>`| 所有當地語系化的套件中繼資料包含的項目

### <a name="metadata-element"></a>中繼資料元素

內`<Metadata>`項目可以有下列項目：

|標題|描述|
|-----------|-----------------|
|`<DisplayName>`|安裝延伸模組的當地語系化的名稱|
|`<Description>`|安裝延伸模組的當地語系化的描述|
|`<License>`| 延伸模組授權的當地語系化版本的路徑|
|`<MoreInfo>`| 有關擴充功能的當地語系化資訊的連結|
|`<ReleaseNotes>`| 路徑或通往當地語系化版本的版本資訊|
|`<Icon>`| 當地語系化版本的擴充功能圖示路徑|

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

|標題|描述|
|-----------|-----------------|
|[將 VSIX 封裝當地語系化](../extensibility/localizing-vsix-packages.md)|示範如何提供當地語系化的安裝支援 VSIX 套件。|
|[VSIX 延伸結構描述 2.0 參考](../extensibility/vsix-extension-schema-2-0-reference.md)|VSIX 資訊清單描述的內容 *.vsix*部署檔案。 部署檔案可讓您使用安裝 Visual Studio 擴充功能**擴充功能和更新** 對話方塊。|
|[尋找和使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)|示範如何使用**擴充功能和更新**對話方塊，即可安裝、 移除、 啟動及停用延伸模組。|