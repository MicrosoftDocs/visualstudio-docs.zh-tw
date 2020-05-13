---
title: 預設命令、組與工具列放置 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b432b514231e876dda1393bad8a315030272d998
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708896"
---
# <a name="default-command-group-and-toolbar-placement"></a>預設命令、群組與工具列放置
為使產品均勻性和穩定性,UI 默認顯示某些命令組,併[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]為 命令和命令組提供定義。 VS包也可以使用標準命令和命令組。

 默認命令組分為三類:IDE 命令、產品命令和編輯器命令。

## <a name="default-ide-commands"></a>預設 IDE 命令
 預設 IDE 工具列包括 由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]中包含的 所有產品共用的命令。 其中包括與通用專案操作相關的命令,如 **「保存」** 命令和 **「新增專案」** 命令。 VSPackages 不應從此工具列中添加或減去,但有一個例外:如果產品或 VSPackage 添加了新的工具視窗,則應將視窗添加到 **「視圖」** 功能表上的可用工具視窗清單中。 新產品或 VS 套件可以添加自己的工具列。

## <a name="default-product-commands"></a>預設產品指令
 每個產品都可以為 IDE 提供其自己的預設工具列,其中包含重要且經常使用的命令。 但是,最好盡可能使用現有功能表和工具列,並根據需要使用其他特定於任務的工具列對其進行補充。

 工具列的優先順序欄位確定其行位置。 零優先順序將工具列放在第三行(第 3 行)、功能表列(第 1 行)和**標準**工具列(第 2 行)下方。 因此,其他工具列出現在行(優先順序 = 3)。 如果有空間,則後續工具列將放在同一行上;否則,它們將自動移動到下一行。

## <a name="default-editor-commands"></a>預設編輯器指令
 提供自訂編輯器的 VSPackage 應提供預設工具列,其中包含該編輯器中最重要且最常用的命令。 編輯器工具列應在編輯器處於活動狀態時顯示,並且在編輯器不處於活動狀態時應隱藏。 此可見性控制在`VisibilityConstraints`*.vsct*檔案的元素中。

 編輯器工具列應放在 IDE 和產品工具列下方。

## <a name="see-also"></a>另請參閱
- [IDE 定義的指令、選單和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [VS 套件如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
