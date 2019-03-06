---
title: VisibilityConstraints 元素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c567291f2b91e092afecb264c2b2e0ca1bfd108
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56702573"
---
# <a name="visibilityconstraints-element"></a>VisibilityConstraints 元素
VisibilityConstraints 元素會決定靜態群組的命令和工具列可見。 可見性會先受到[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]沒有載入 VSPackage 的整合式的開發環境 (IDE)。

## <a name="syntax"></a>語法

```xml
<VisibilityConstraints>
  <VisibilityConstraint>... </VisibilityConstraint>
  <VisibilityConstraint>... </VisibilityConstraint>
</VisibilityConstraint>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|[VisibilityItem 元素](../extensibility/visibilityitem-element.md)|決定命令和工具列的靜態可見。|
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|決定靜態群組的命令和工具列可見。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義代表 VSPackage 提供給 IDE 的命令 （例如，功能表項目、 功能表、 工具列和下拉式方塊） 的所有項目。|

## <a name="example"></a>範例

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>另請參閱
- [VisibilityItem 元素](../extensibility/visibilityitem-element.md)
- [Visual Studio 命令表 (。Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)