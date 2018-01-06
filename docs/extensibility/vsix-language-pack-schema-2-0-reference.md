---
title: "VSIX 語言套件 2.0 結構描述參考 |Microsoft 文件"
ms.custom: 
ms.date: 10/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
caps.latest.revision: "8"
ms.author: dagriffe
author: dgriffen
manager: ghogen
ms.workload: dagriffe
ms.openlocfilehash: b601653e4b2d309d41f32ff71666567ab860e698
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="vsix-language-pack-schema-20-reference"></a>VSIX 語言套件 2.0 結構描述參考

VSIX 語言組件的結構描述提供 VSIX 套件的當地語系化的安裝的資訊。 此結構描述的 2.0 版支援額外的當地語系化項目。

## <a name="language-pack-schema"></a>語言組件的結構描述

語言組件檔案的根項目是`<PackageLanguagePackManifest>`，使用的屬性`Version`，這是語言組件格式的版本。 本主題描述的語言組件格式，藉由設定資訊清單中指定的 2.0 版`Version`屬性的值`Version="2.0.0"`。 根項目包含一個子`<Metadata>`項目。

### <a name="packagelangaugepackmanifest-element"></a>PackageLangaugePackManifest 項目

內`<PackageLanguagePackManifest>`項目必須存在下列項目：
|標題|描述|
|-----------|-----------------|
|`<Metadata>`| 所有當地語系化的封裝中繼資料包含的項目

### <a name="metadata-element"></a>中繼資料元素

內`<Metadata>`元素可以具有下列元素：
|標題|描述|
|-----------|-----------------|
|`<DisplayName>`|安裝擴充功能的當地語系化的名稱|
|`<Description>`|若要安裝擴充功能的當地語系化的說明|
|`<License>`| 擴充功能的授權的當地語系化版本的路徑|
|`<MoreInfo>`| 當地語系化延伸模組的相關資訊的連結|
|`<ReleaseNotes>`| 路徑或通往當地語系化版本的版本資訊|
|`<Icon>`| 當地語系化版本的擴充功能圖示的路徑|

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

## <a name="see-also"></a>請參閱

|標題|描述|
|-----------|-----------------|
|[將 VSIX 封裝當地語系化](../extensibility/localizing-vsix-packages.md)|示範如何提供當地語系化的安裝支援 VSIX 套件。|
|[VSIX 擴充功能結構描述 2.0 參考](../extensibility/vsix-extension-schema-2-0-reference.md)|VSIX 資訊清單描述可讓使用來安裝的 Visual Studio 擴充功能之.vsix 部署檔案內容**擴充功能和更新** 對話方塊。|
|[尋找和使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)|示範如何使用**擴充功能和更新**對話方塊，即可安裝、 移除、 啟用以及停用擴充功能。|