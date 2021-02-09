---
title: 命令元素 |Microsoft Docs
description: 命令元素代表 VSPackage 工具列上的命令集合，而且可以有下列區段：功能表、群組、按鈕、combos 和點陣圖。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90670188e3ce1aa621e53c69bad6f795ff30fd8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887428"
---
# <a name="commands-element"></a>Commands 項目
代表 VSPackage 工具列上的命令集合。 集合最多可有五個子區段，如下所示：功能表、群組、按鈕、combos 和點陣圖。

 例如，每個子項目 \<Menu> 都是由 GUID 和數位識別碼組的唯一命令識別碼所識別。 GUID 會識別「命令集」，用來將邏輯上相關的命令分組。 VSPackage 應該定義自己的命令集，以避免與其他 Vspackage 所定義的命令識別碼發生衝突。

## <a name="syntax"></a>Syntax

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

|屬性|說明|
|---------------|-----------------|
|套件|GUID，可識別提供命令的 VSPackage。<br /><br /> 例如，package = "guidVsPackage1Pkg"。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[Menu 元素](../extensibility/menus-element.md)|定義 VSPackage 所實行的所有功能表。|
|[Groups 元素](../extensibility/groups-element.md)|包含在 VSPackage 中定義命令群組的專案。|
|[按鈕元素](../extensibility/buttons-element.md)|群組按鈕元素。|
|[點陣圖元素](../extensibility/bitmaps-element.md)|群組點陣圖元素。|
|[Combos 元素](../extensibility/combos-element.md)|群組組合元素。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義代表 VSPackage 提供給 IDE 之命令的所有元素。 可能的元素是功能表項目、功能表、工具列和下拉式方塊。|

## <a name="example"></a>範例
 下列範例示範如何使用 [命令元素](../extensibility/commands-element.md)。

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
- [Vspackage 如何新增使用者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
