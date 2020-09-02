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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1aaa9573b883910ac6fa5d921a9bc79ce1c1cf3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698197"
---
# <a name="visibilityconstraints-element"></a>VisibilityConstraints 元素
VisibilityConstraints 元素決定了命令和工具列群組的靜態可見度。 可見度是在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 不載入 VSPackage 的情況下，由整合式開發環境 (IDE) 所控制。

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
|條件|選擇性。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|[VisibilityItem 元素](../extensibility/visibilityitem-element.md)|決定命令和工具列的靜態可見度。|
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|決定命令和工具列群組的靜態可見度。|

### <a name="parent-elements"></a>父元素

|項目|描述|
|-------------|-----------------|
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義代表命令 (的所有元素，例如，功能表項目、功能表、工具列，以及 VSPackage 提供給 IDE) 的下拉式方塊。|

## <a name="example"></a>範例

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>另請參閱
- [VisibilityItem 元素](../extensibility/visibilityitem-element.md)
- [Visual Studio 命令表格 (。.Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
