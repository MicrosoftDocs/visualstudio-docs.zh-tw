---
title: 命令項目 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab8629fb3ef83277f1366a5141c400b8eeea70e3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341906"
---
# <a name="commands-element"></a>Commands 元素
表示 [VSPackage] 工具列上的命令的集合。 集合可以有最多五個小節中，如下： 功能表、 群組、 按鈕、 combos，與點陣圖。

 每個小節子項目，例如\<功能表 >，由 GUID 和數字識別元組的唯一命令 ID。 GUID 識別的 「 命令集 」，用來分組邏輯相關的命令。 VSPackage，應該定義自己的命令集，以避免與其他 Vspackage 所定義的命令 Id 的衝突。

## <a name="syntax"></a>語法

```xml
<Commands package="GuidMyPackage" >
  <Menus>... </Menus>
  <Groups>... </Groups>
  <Buttons>... </Buttons>
  <Combos>... </Combos>
  <Bitmaps>... </Bitmaps>
</Commands>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|套件|識別提供命令的 VSPackage 的 GUID。<br /><br /> 例如，封裝 ="guidVsPackage1Pkg 」。|

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|[功能表項目](../extensibility/menus-element.md)|定義實作 VSPackage 的所有功能表。|
|[Groups 元素](../extensibility/groups-element.md)|包含在 VSPackage 中定義的命令群組的項目。|
|[Buttons 元素](../extensibility/buttons-element.md)|分組按鈕項目。|
|[Bitmaps 元素](../extensibility/bitmaps-element.md)|分組點陣圖項目。|
|[Combos 元素](../extensibility/combos-element.md)|分組下拉式項目。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義代表 VSPackage 提供給 IDE 命令的所有項目。 可能的項目是功能表項目、 功能表、 工具列和下拉式方塊。|

## <a name="example"></a>範例
 下列範例示範如何使用[Commands 元素](../extensibility/commands-element.md)。

```
<Commands package="guidMyPackage">
    <Menus>
      <Menu Condition="'%(DEBUG)' != 'true'"
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"
        priority="0x0000" type="Menu">
        <Annotation>
          <Documentation>this is an annotation</Documentation>
          <AppInfo>
            <CustomData>
              <CustomSubElement>Some data</CustomSubElement>
            </CustomData>
          </AppInfo>
        </Annotation>
        <CommandFlag>AlwaysCreate</CommandFlag>
        <Strings>
          <ButtonText>MainMenu</ButtonText>
        </Strings>
      </Menu>
  </Menus>
<Commands>
```

## <a name="see-also"></a>另請參閱
- [Vspackage 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)