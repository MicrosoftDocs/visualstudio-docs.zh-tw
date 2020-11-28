---
title: 命令放置指導方針 |Microsoft Docs
description: 瞭解在 Visual Studio 整合式開發環境 (IDE) 中放置命令的指導方針和最佳作法。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 11a1619eaa625e086ac93bfa0f9e208239f8c844
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305249"
---
# <a name="command-placement-guidelines"></a>命令放置指導方針
在 Visual Studio 整合式開發環境中放置命令的最佳作法 (IDE) 依命令集的大小而有所不同。 命令會根據 *.vsct* 檔案中的資訊來定義和定位。

## <a name="best-practices-for-all-command-sets"></a>所有命令集的最佳作法
 針對每一組命令，請遵循下列指導方針：

- 事先準備命令結構的圖表。 識別將在多個位置使用的命令、下拉式方塊、命令群組和快捷方式功能表。

- 出現在相同群組中的命令應該會相關。

- 可以接受只包含一個命令的群組。

- 套件不應將許多命令新增至現有的 Visual Studio 功能表中。 相反地，他們應該建立功能表或子功能表來裝載新的命令。

- 當您在現有的功能表上放入命令時，請將命令命名，使其目的更清楚，而且不會與現有的命令混淆。

## <a name="best-practices-for-small-command-sets"></a>小型命令集的最佳作法
 如果您正在開發只有一些命令的 VSPackage，也請遵循下列指導方針：

- 可能的話，請使用命令、下拉式方塊、群組或子功能表的 [父](../../extensibility/parent-element.md) 元素，將它放在適當的群組中。

- 將這些群組指派給 VSPackage 所顯示的功能表。

- 子功能表或命令的父系必須是 [Group](../../extensibility/group-element.md) 元素。 將命令和子功能表指派給群組，然後將群組指派給父功能表。

- 您可以藉由在命令的定義之後新增 [CommandPlacements](../../extensibility/commandplacements-element.md) 元素區段，然後將 `CommandPlacements` 每個額外群組的 [CommandPlacement](../../extensibility/commandplacement-element.md) 專案新增至專案，將命令放在其他群組中。

## <a name="best-practices-for-large-command-sets"></a>大型命令集的最佳作法
 如果您的 VSPackage 會有許多將出現在多個內容中的命令，也請遵循下列指導方針：

- 讓功能表、群組和命令成為自我父代。 也就是說，請勿 `Parent` 在專案的定義中指派專案。

- 使用 `CommandPlacement` 元素區段中的專案專案，將 `CommandPlacements` 功能表、群組和命令放在其父功能表和群組中。

- 在 [ `CommandPlacements` 元素] 區段中，填入指定功能表或群組的專案應該彼此相鄰。 這有助於提高可讀性，並讓 `Priority` 排名更容易判斷。

## <a name="see-also"></a>另請參閱
- [Vspackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Visual Studio 命令表格 (. .vsct) 檔](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
