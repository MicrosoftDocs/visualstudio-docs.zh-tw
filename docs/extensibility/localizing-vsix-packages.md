---
title: 本地化 VSIX 套件 ( A)微軟文件
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d2d4222e45d56447951e86d558af9983a0d1cc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702891"
---
# <a name="localizing-vsix-packages"></a>將 VSIX 套件當地語系化

您可以透過為每個目標語言建立*擴展.vsixlangpack*檔案,然後將它們放在正確的資料夾中來當地語系化 VSIX 套件。 安裝當地語系化包時,擴展的本地化名稱將與本地化說明一起顯示。 如果提供當地語系化許可證檔或指向當地語系化資訊的 URL,也會顯示這些檔。

如果 VSIX 包的內容包含添加選單命令或其他 UI 的 VSPackage,請參閱[本地化選單命令](../extensibility/localizing-menu-commands.md),瞭解有關本地化新 UI 元素的資訊。

## <a name="directory-structure"></a>目錄結構

 當使用者安裝延伸時,**擴展和更新**會檢查其名稱與目標電腦的 Visual Studio 區域設定匹配的資料夾的 VSIX 包的頂層。 如果**擴展和更新**在資料夾中找到 *.vsixlangpack*檔案,它將該檔中的本地化值替換為 *.vsixmanifest*檔中的相應值。 安裝擴展時將顯示這些值。 下面的範例顯示了當地語化為西班牙文 (es-ES) 和法語 (fr-FR) 的 VSIX 套件的目錄結構。

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
> 中支援 VSIX 的專案[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]樣本 產生 VSIX 清單並將使用*source.延伸.vsixmanifest*。 當 Visual Studio 生成專案時,它會將該檔的內容複製到 VSIX 套件中的擴展.VsixManifest 中。

## <a name="the-extensionvsixlangpack-file"></a>延伸.vsixlangpack 檔案

*延伸.vsixlangpack*檔案遵循[VSIX 語言套件架構 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md)。 此架構具有`PackageLanguagePackManifest`, 它緊接`Metadata`子 元素。 中繼資料元素最多可以包含 6`DisplayName`個`Description``MoreInfo``License``ReleaseNotes`子`Icon`元素 、、、、、、、、、、、、 與 。 這些子`DisplayName``Description`元素`MoreInfo``License``ReleaseNotes`對應於*擴展.vsixmanifest*檔案元素`Icon`的`Metadata`子元素。

建立 vsixlangpack 檔案時,`Include in Vsix`必須將`true`屬性設定為 。 否則,將忽略當地語系化的安裝文本。

### <a name="to-set-the-include-in-vsix-property"></a>在 Vsix 屬性中設置"包括"

1. 在**解決方案資源管理員**中,右鍵按一次延伸.vsixlangpack 檔案,然後按下**屬性**。

2. 屬性**格線**中,按下**Vsix 中的「包括**」,並將`true`其值設定為 。

## <a name="example"></a>範例

### <a name="description"></a>描述

下面的範例顯示*擴展.vsixmanifest*文件的相關部分。 該檔還包括西班牙文的相應*擴展.vsixlangpack*檔案。 如果目標電腦的 Visual Studio 區域設置設定為西班牙文,則語言包中的值將替換清單中的值。

### <a name="code"></a>程式碼

- [*延伸.vsixmanifest]*

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

- 【*延伸.vsixlangpack*]

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

|Title|描述|
|-----------|-----------------|
|[VSIX 語言套件架構 2.0 參考](vsix-language-pack-schema-2-0-reference.md)|VSIX 語言包描述 .v6 部署檔的當地語系化資訊。|
|[VSIX 套件的分析](../extensibility/anatomy-of-a-vsix-package.md)|描述 vsix 包的結構和內容。|
|[本地化選單指令](../extensibility/localizing-menu-commands.md)|展示如何本地化擴展中的其他文本資源。|
