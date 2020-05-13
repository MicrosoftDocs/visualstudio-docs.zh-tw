---
title: 命令放置指南 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 021a5fd9f9931e3041a431d211c8ab49978bbbab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709560"
---
# <a name="command-placement-guidelines"></a>命令放置指南
在 Visual Studio 整合式開發環境 (IDE) 中定位命令的最佳做法因命令集的大小而異。 命令根據 *.vsct*檔案中的資訊定義和定位。

## <a name="best-practices-for-all-command-sets"></a>所有指令集的最佳做法
 對於每組命令,請遵循以下準則:

- 提前準備命令結構圖表。 標識將在多個位置使用的命令、組合框、命令組和快捷功能表。

- 出現在同一組中的命令應相關。

- 只包含一個命令的組是可以接受的。

- 包不應向現有 Visual Studio 功能表添加大量命令。 相反,他們應該創建功能表或子菜單來承載新命令。

- 將命令放在現有功能表上時,命名該命令,使其用途明確,並且不會與現有命令混淆。

## <a name="best-practices-for-small-command-sets"></a>小型指令集的最佳做法
 如果您正在開發一個僅包含幾個命令的 VSPackage,請遵循以下準則:

- 如果可能,請使用命令、組合框、組或子功能表的[父](../../extensibility/parent-element.md)元素將其放入相應的組中。

- 將這些組分配給 VSPackage 顯示的功能表。

- 子功能表或命令的父級必須是[組](../../extensibility/group-element.md)元素。 將命令和子功能表分配給組,然後將組分配給父菜單。

- 通過在指令定義後添加[命令放置](../../extensibility/commandplacements-element.md)元素部分,然後將命令`CommandPlacements`添加到 元素中,從而將命令放入其他[CommandPlacement](../../extensibility/commandplacement-element.md)組中。

## <a name="best-practices-for-large-command-sets"></a>大型指令集的最佳做法
 如果您的 VSPackage 將有許多指令會顯示在多個上下文中,請遵循以下準則:

- 使功能表、組和命令自父母。 也就是說,不要在項的定義中`Parent`分配元素。

- 使用`CommandPlacement``CommandPlacements`元素部分中的元素條目將功能表、組和命令放在其父功能表和組中。

- 在`CommandPlacements`元素部分中,填充給定菜單或組的條目應彼此相鄰。 這有助於可讀性,`Priority`使排名更容易確定。

## <a name="see-also"></a>另請參閱
- [VS 套件如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [視覺化工作室指令表 (.vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
