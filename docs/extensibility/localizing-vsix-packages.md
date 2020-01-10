---
title: 當地語系化 VSIX 封裝 |Microsoft Docs
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 171c8635c2d6db2c346fb836701e630812ecbb28
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186450"
---
# <a name="localizing-vsix-packages"></a>將 VSIX 套件當地語系化

您可以藉由為每個目的語言建立*vsixlangpack*檔案，然後將它們放在正確的資料夾中，來當地語系化 VSIX 封裝。 安裝當地語系化的封裝時，延伸模組的當地語系化名稱會連同當地語系化的描述一起顯示。 如果您提供當地語系化的授權檔案，或指向當地語系化資訊的 URL，則也會顯示這些檔案。

如果您的 VSIX 套件包含可新增功能表命令或其他 UI 的 VSPackage，請參閱將[功能表命令當地語系化](../extensibility/localizing-menu-commands.md)以取得當地語系化新 UI 元素的相關資訊。

## <a name="directory-structure"></a>目錄結構

 當使用者安裝延伸模組時，**延伸模組和更新**會檢查其名稱符合目的電腦的 Visual Studio 地區設定之資料夾的最上層 VSIX 封裝。 如果**擴充功能和更新**在資料夾中找到*vsixlangpack*檔案，則會將該檔案中的當地語系化值替換為*extension.vsixmanifest*檔案中的對應值。 安裝延伸模組時，會顯示這些值。 下列範例會顯示當地語系化為西班牙文（es）和法文（fr-fr）之 VSIX 封裝的目錄結構。

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 中的 VSIX 支援專案範本會產生 VSIX 資訊清單，並將其命名為*extension.vsixmanifest*。 當 Visual Studio 建立專案時，它會將該檔案的內容複寫到 VSIX 封裝中的 Extension.vsixmanifest。

## <a name="the-extensionvsixlangpack-file"></a>Vsixlangpack 檔案

*Vsixlangpack*檔案遵循[VSIX 語言套件架構 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md)。 此架構具有 `PackageLanguagePackManifest`，其後面緊接著 `Metadata` 子項目。 Metadata 元素最多可以包含6個子項目，`DisplayName`、`Description`、`MoreInfo`、`License`、`ReleaseNotes`和 `Icon`。 這些子項目會對應至*extension.vsixmanifest*檔案之 `ReleaseNotes`元素的 `DisplayName`、`Description`、`MoreInfo`、`License`、`Icon` 和 `Metadata` 子項目。

當您建立 vsixlangpack 檔案時，您必須將 `Include in Vsix` 屬性設定為 [`true`]。 否則，將會忽略當地語系化的安裝文字。

### <a name="to-set-the-include-in-vsix-property"></a>若要設定在 Vsix 屬性中包含

1. 在**方案總管**中，以滑鼠右鍵按一下 vsixlangpack 檔案，然後按一下 [**屬性**]。

2. 在**屬性方格**中，按一下 [**包含在 Vsix 中**]，並將其值設定為 `true`。

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例會顯示*extension.vsixmanifest*檔案的相關部分。 此檔案也包含適用于西班牙文的對應*副檔名 vsixlangpack*檔案。 如果目的電腦的 Visual Studio 地區設定設為西班牙文，語言套件中的值會取代資訊清單中的值。

### <a name="code"></a>程式碼

- [*Extension. extension.vsixmanifest*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

- [*Extension. vsixlangpack*]

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
|[VSIX 語言套件架構2.0 參考](vsix-language-pack-schema-2-0-reference.md)|VSIX 語言套件會描述 .vsix 部署檔案的當地語系化資訊。|
|[VSIX 封裝的剖析](../extensibility/anatomy-of-a-vsix-package.md)|描述 vsix 封裝的結構和內容。|
|[將功能表命令當地語系化](../extensibility/localizing-menu-commands.md)|顯示如何將延伸模組中的其他文字資源當地語系化。|