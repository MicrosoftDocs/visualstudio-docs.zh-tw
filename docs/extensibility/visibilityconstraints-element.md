---
title: 可見性約束元素 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1aaa9573b883910ac6fa5d921a9bc79ce1c1cf3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698197"
---
# <a name="visibilityconstraints-element"></a>可見性限制元素
"可見性約束"元素確定命令組和工具列組的靜態可見性。 可見性首先由[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]整合式開發環境 (IDE) 控制,無需載入 VSPackage。

## <a name="syntax"></a>語法

```xml
<VisibilityConstraints>
  <VisibilityItem />
  <VisibilityItem />
</VisibilityConstraints>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|條件|選擇性。 請參考[條件屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[可見性項目元素](../extensibility/visibilityitem-element.md)|確定命令和工具列的靜態可見性。|
|[可見性限制](../extensibility/visibilityconstraints-element.md)|確定命令組和工具列的靜態可見性。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[指令表元素](../extensibility/commandtable-element.md)|定義表示 VSPackage 向 IDE 提供的命令的所有元素(例如,功能表項、功能表、工具列和組合框)。|

## <a name="example"></a>範例

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>另請參閱
- [可見性項目元素](../extensibility/visibilityitem-element.md)
- [視覺化工作室命令表 (.Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
