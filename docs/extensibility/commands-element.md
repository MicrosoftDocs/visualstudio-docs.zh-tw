---
title: 指令元素 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ea2400cca19a02475caecec3d022e0b78794ae4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739681"
---
# <a name="commands-element"></a>Commands 項目
表示 VSPackage 工具列上的命令集合。 集合最多可以有五個子節,如下所示:功能表、組、按鈕、組合和位圖。

 每個子節子元素(例如,\<選單>)都由一個唯一的命令 ID 標識,該 ID 是 GUID 和數位識別碼對。 GUID 識別"命令集",用於對邏輯相關命令進行分組。 VSPackage 應定義自己的命令集,以避免與其他 VSPackage 定義的命令指示號發生衝突。

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
|套件|標識提供命令的 VSPackage 的 GUID。<br /><br /> 例如,包="guidV 包1Pkg"。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[選單元素](../extensibility/menus-element.md)|定義 VSPackage 實現的所有功能表。|
|[群組項目](../extensibility/groups-element.md)|包含在 VSPackage 中定義命令組的項目。|
|[按鈕項目](../extensibility/buttons-element.md)|對按鈕元素進行分組。|
|[點陣圖元素](../extensibility/bitmaps-element.md)|對位圖元素。|
|[組合項目](../extensibility/combos-element.md)|對組合元素進行分組。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[指令表元素](../extensibility/commandtable-element.md)|定義表示 VS 包向 IDE 提供的命令的所有元素。 可能的元素是功能表項、功能表、工具列和組合框。|

## <a name="example"></a>範例
 下面的範例展示如何使用[指令元素](../extensibility/commands-element.md)。

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
- [VS 套件如何新增使用者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [命令、選單和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
