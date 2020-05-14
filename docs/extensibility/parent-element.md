---
title: 父元素 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c018505ba06762bf8426f266b24ee1835313c29
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702221"
---
# <a name="parent-element"></a>父元素
按鈕或組合框的父項可能只有組。 功能表或組的父項可以是任何其他功能表或組。 在[命令放置元素中](../extensibility/commandplacement-element.md),需要此元素;在所有其他實例中,它是可選的。 如果省略此元素,則表示的`Group_Undefined:0`父元素。

## <a name="syntax"></a>語法

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|guid|必要。 GUID/ID 命令識別碼的 GUID。|
|id|必要。 GUID/ID 命令識別碼的識別碼。|

### <a name="child-elements"></a>子元素
 None

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[指令表元素](../extensibility/commandtable-element.md)|定義表示 VS 套件向整合式開發環境 (IDE) 提供的命令的所有元素。 例如,功能表項、功能表、工具列和組合框。|
|[按鈕項目](../extensibility/buttons-element.md)|對[按鈕元素](../extensibility/button-element.md)進行分組。|
|[選單元素](../extensibility/menus-element.md)|定義 VSPackage 實現的所有功能表。|
|[群組項目](../extensibility/groups-element.md)|包含定義 VSPackage 的命令組的條目。|

## <a name="see-also"></a>另請參閱
- [視覺化工作室指令表 (.vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
