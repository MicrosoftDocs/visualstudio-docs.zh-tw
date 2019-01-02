---
title: 將 VSIX 封裝當地語系化 |Microsoft Docs
ms.custom: ''
ms.date: 10/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85d32f25e8dd1f2f56af0857f2be0ff24c4d3126
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2018
ms.locfileid: "53740243"
---
# <a name="localizing-vsix-packages"></a>將 VSIX 套件當地語系化

您可以將 VSIX 封裝當地語系化藉由建立*Extension.vsixlangpack*針對每個目標語言檔案，然後再將它們放入正確的資料夾。 安裝當地語系化的套件時，延伸模組的當地語系化的名稱會顯示與當地語系化的描述。 如果您提供當地語系化的授權檔案或指向當地語系化資訊的 URL，也會顯示它們。

如果內容 VSIX 封裝包含 VSPackage 將功能表命令或其他 UI，請參閱[當地語系化功能表命令](../extensibility/localizing-menu-commands.md)如需當地語系化新的 UI 項目。

## <a name="directory-structure"></a>目錄結構

 當使用者安裝延伸模組，**擴充功能和更新**檢查最高層級的 VSIX 封裝，其名稱符合 Visual Studio 電腦的地區設定目標的資料夾。 如果**擴充功能和更新**尋找 *.vsixlangpack*檔案的資料夾中，它會取代該檔案中的對應值的當地語系化的值 *.vsixmanifest*檔案。 正在安裝延伸模組時，會顯示這些值。 下列範例顯示 VSIX 封裝當地語系化為西班牙文 (ES-ES) 和法文 (FR-FR) 的目錄結構。  

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
> 中的 VSIX 支援的專案範本[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]產生的 VSIX 資訊清單並將它命名*source.extension.vsixmanifest*。 當 Visual Studio 會建置專案時，它會複製該檔案的內容到 Extension.VsixManifest VSIX 封裝中。

## <a name="the-extensionvsixlangpack-file"></a>Extension.vsixlangpack 檔案

*Extension.vsixlangpack*檔案如下所示[VSIX 語言套件結構描述 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md)。 此結構描述`PackageLanguagePackManifest`，這會緊跟著`Metadata`子項目。 中繼資料元素可以包含最多 6 個的子項目， `DisplayName`， `Description`， `MoreInfo`， `License`， `ReleaseNotes`，和`Icon`。 這些子元素會對應至`DisplayName`， `Description`， `MoreInfo`， `License`， `ReleaseNotes`，和`Icon`子項目的`Metadata`項目*Extension.vsixmanifest*檔案。

當您建立 vsixlangpack 檔案時，您必須設定`Include in Vsix`屬性設`true`。 否則，會忽略的當地語系化的安裝文字。

### <a name="to-set-the-include-in-vsix-property"></a>若要設定包含在 Vsix 屬性

1. 在 **方案總管**Extension.vsixlangpack 檔案中，按一下滑鼠右鍵，然後按一下 **屬性**。

2.  在 **屬性方格**，按一下**Include in Vsix**，並將其值設定為`true`。

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例顯示的相關部分*Extension.vsixmanifest*檔案。 該檔案也包含對應*Extension.vsixlangpack*西班牙文的檔案。 如果 Visual Studio 電腦的地區設定目標設定為西班牙文語言套件中的值就會取代從資訊清單的值。

### <a name="code"></a>程式碼

 [*Extension.vsixmanifest*]

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

 [*Extension.vsixlangpack*]

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

## <a name="see-also"></a>另請參閱

|標題|描述|
|-----------|-----------------|
|[VSIX 語言套件結構描述 2.0 參考](/visualstudio/extensibility/vsix-language-pack-schema-2-0-reference)|VSIX 語言套件描述.vsix 部署檔案的當地語系化資訊。|
|[VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)|Vsix 封裝的內容與結構描述。|
|[將功能表命令當地語系化](../extensibility/localizing-menu-commands.md)|示範如何將延伸模組中的其他文字資源當地語系化。|