---
title: Parent 元素 |Microsoft Docs
description: 父元素會指定專案是按鈕、下拉式方塊、功能表或群組的父系。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3dbf7202ac7fb94762ea132a2620625fae97ddfb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901548"
---
# <a name="parent-element"></a>父元素
按鈕或下拉式方塊的父系可能只是群組。 功能表或群組的父系可以是任何其他功能表或群組。 在 [CommandPlacement 元素](../extensibility/commandplacement-element.md)中，需要這個元素。在其他所有實例中，則是選擇性的。 如果省略這個元素，就會隱含的父系 `Group_Undefined:0` 。

## <a name="syntax"></a>Syntax

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|guid|必要。 GUID/識別碼命令識別碼的 GUID。|
|id|必要。 GUID/識別碼命令識別碼的識別碼。|

### <a name="child-elements"></a>子元素
 無

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義代表 VSPackage 提供給整合式開發環境 (IDE) 命令的所有元素。 例如，功能表項目、功能表、工具列和下拉式方塊。|
|[按鈕元素](../extensibility/buttons-element.md)|群組 [按鈕元素](../extensibility/button-element.md) 元素。|
|[Menu 元素](../extensibility/menus-element.md)|定義 VSPackage 所實行的所有功能表。|
|[Groups 元素](../extensibility/groups-element.md)|包含定義 VSPackage 之命令群組的專案。|

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表格 (. .vsct) 檔](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
