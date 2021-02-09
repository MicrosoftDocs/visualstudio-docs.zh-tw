---
title: 預設命令、群組和工具列位置 |Microsoft Docs
description: 瞭解 Visual Studio 使用者介面預設顯示的 IDE 命令、產品命令和編輯器命令。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1c38abc09b0d5c8996cde44d33f4778a54a0cd62
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902959"
---
# <a name="default-command-group-and-toolbar-placement"></a>預設命令、群組和工具列位置
針對產品一致性和穩定性，UI 預設會顯示特定的命令群組，並 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供命令和命令群組的定義。 Vspackage 也可以使用標準命令和命令群組。

 預設的命令群組分為三個類別： IDE 命令、產品命令和編輯器命令。

## <a name="default-ide-commands"></a>預設 IDE 命令
 預設的 IDE 工具列包含中包含的所有產品所共用的命令 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 這些包括與一般專案作業相關的命令，例如 [ **儲存** ] 命令和 [ **新增專案** ] 命令。 Vspackage 不應該加入或減去這個工具列，但有一個例外：如果 product 或 VSPackage 加入了新的工具視窗，則應該將視窗加入 [ **View** ] 功能表上可用的工具視窗清單中。 新產品或 Vspackage 可以加入自己的工具列。

## <a name="default-product-commands"></a>預設產品命令
 每項產品都可以提供 IDE 自己的預設工具列，其中包含重要且常用的命令。 不過，最好盡可能使用現有的功能表和工具列，並視需要使用其他工作專屬的工具列來補充它們。

 工具列的 [優先順序] 欄位會決定其資料列位置。 零優先權會將工具列放在第三個數據列的第三個數據列上 (資料列 3) 的功能表列下方 (列 1) 和 **標準** 工具列 (資料列 2) 。 因此，其他工具列會顯示在資料列 (優先順序 + 3) 。 後續的工具列會放在同一個資料列上，如果有空間，否則，它們會自動移至下一個資料列。

## <a name="default-editor-commands"></a>預設編輯器命令
 提供自訂編輯器的 VSPackage 應該提供預設工具列，其中包含該編輯器中最重要且最常使用的命令。 當編輯器為使用中狀態時，編輯器工具列應該會出現，而且當編輯器非使用中時應該隱藏。 此可見度是在 .vsct 檔案的 `VisibilityConstraints` 元素中控制。

 編輯器工具列應放置在 [IDE] 和 [產品] 工具列下方。

## <a name="see-also"></a>另請參閱
- [IDE 定義的命令、功能表和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [Vspackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
