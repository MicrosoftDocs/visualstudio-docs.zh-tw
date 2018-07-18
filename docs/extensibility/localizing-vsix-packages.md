---
title: 當地語系化 VSIX 封裝 |Microsoft 文件
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
ms.openlocfilehash: d94e390374ca2eb77b4332b3a5c253acce69f051
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143409"
---
# <a name="localizing-vsix-packages"></a>當地語系化 VSIX 封裝

您可以當地語系化 VSIX 封裝，建立每個目標語言的 Extension.vsixlangpack 檔案，然後將它們放在正確的資料夾。 安裝當地語系化的封裝時，延伸模組的當地語系化的名稱會顯示與當地語系化的描述。 如果您提供當地語系化的授權檔案或指向當地語系化資訊的 URL，也會顯示它們。

如果內容包含 VSIX 封裝加入功能表命令或其他 UI，請參閱[當地語系化功能表命令](../extensibility/localizing-menu-commands.md)有關當地語系化新的 UI 項目。

## <a name="directory-structure"></a>目錄結構

 當使用者安裝擴充功能，**擴充功能和更新**檢查 VSIX 封裝的資料夾名稱符合目標電腦的 Visual Studio 地區設定的最上層。 如果**擴充功能和更新**a.vsixlangpack 尋找檔案的資料夾中，以取代該檔案的.vsixmanifest 檔案中的對應值的當地語系化的值。 正在安裝擴充功能時，會顯示這些值。 下列範例會顯示當地語系化成西班牙文 (ES-ES) 和法文 (FR-FR) VSIX 封裝的目錄結構。  

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
> 中的 VSIX 支援專案範本[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]產生 VSIX 資訊清單並將它命名為 source.extension.vsixmanifest。 當 Visual Studio 建置專案時，會複製該檔案的內容至 Extension.VsixManifest VSIX 封裝中。

## <a name="the-extensionvsixlangpack-file"></a>Extension.vsixlangpack 檔案

Extension.vsixlangpack 檔會遵循[VSIX 語言組件的結構描述 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md)。 此結構描述具有`PackageLanguagePackManifest`，它會緊接著`Metadata`子項目。 中繼資料元素可以包含最多 6 的子項目`DisplayName`， `Description`， `MoreInfo`， `License`， `ReleaseNotes`，和`Icon`。 這些子元素對應到`DisplayName`， `Description`， `MoreInfo`， `License`， `ReleaseNotes`，和`Icon`子項目的`Metadata`Extension.vsixmanifest 檔案項目。

當您建立 vsixlangpack 檔案時，您必須設定`Include in Vsix`屬性`true`。 否則，將忽略的當地語系化的安裝文字。

### <a name="to-set-the-include-in-vsix-property"></a>若要設定 Vsix 屬性中的 包含

1. 在**方案總管 中**Extension.vsixlangpack 檔案，以滑鼠右鍵按一下，然後按**屬性**。

2.  在屬性方格中，按一下**包含在 Vsix 中的**，並將其值設定為`true`。

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例會顯示相關部分 Extension.vsixmanifest 檔案，以及對應 Extension.vsixlangpack 檔案西班牙文。 如果目標電腦的 Visual Studio 地區設定設定為西班牙文語言組件中的值會取代從資訊清單的值。

### <a name="code"></a>程式碼

 [Extension.vsixmanifest]

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

 [Extension.vsixlangpack]

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
|[VSIX LanguagePack 結構描述 2.0 參考](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|VSIX 語言套件描述.vsix 部署檔案的當地語系化資訊。|
|[VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)|Vsix 套件的內容與結構描述。|
|[將功能表命令當地語系化](../extensibility/localizing-menu-commands.md)|示範如何以當地語系化其他文字中的資源擴充功能。|