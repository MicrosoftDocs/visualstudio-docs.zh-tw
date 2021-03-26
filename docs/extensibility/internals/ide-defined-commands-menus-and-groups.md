---
title: IDE-Defined 命令、功能表和群組 |Microsoft Docs
description: 瞭解 Visual Studio 整合式開發環境中定義的功能表、命令和命令群組 (IDE) 。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b88bbab9c92cdd8627521eaa58284fd33964b7e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085945"
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE 定義的命令、功能表和群組
許多功能表、命令和命令群組已定義為可供 IDE 使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 當您擴充時，也可以使用這些命令 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

## <a name="finding-environment-defined-commands"></a>尋找 Environment-Defined 命令
 環境命令是定義在一組四個 .vsct 檔案中：

- SharedCmdDef. .vsct

- SharedCmdPlace. .vsct

- ShellCmdDef. .vsct

- ShellCmdPlace. .vsct

  這些檔案位於 \VisualStudioIntegration\Common\Inc 中 *\<Visual Studio SDK installation path>* \\ 。 這些檔案會提供功能表和群組的定義和 Guid，您可以在 VSPackage 的命令資料表設定 ( .vsct) 檔中，將其作為您自己的功能表、群組和命令的容器。

## <a name="in-this-section"></a>本節內容
- [Visual Studio 功能表的 GUID 和識別碼](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 提供 [Visual Studio] 功能表列上功能表的 GUID 和識別碼值，以及它們所包含的群組。

- [Visual Studio 工具列的 GUID 和識別碼](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 在 Visual Studio IDE 中提供工具列的 GUID 和識別碼值，以及它們所包含的群組。

- [Visual Studio 命令的 GUID 和識別碼](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 提供 Visual Studio IDE 所定義之命令的 GUID 和識別碼值。

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表檔案 (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [用來擴充專案系統的 IDE 定義的命令](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [VSPackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
