---
title: IDE 定義的命令、功能表和群組 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af6d3e180e2b3d5eb2e0f6c85b7488761e160c69
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727289"
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE 定義的命令、功能表和群組
已定義許多功能表、命令和命令群組供 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 使用。 當您擴充 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 時，也可以使用這些命令。

## <a name="finding-environment-defined-commands"></a>尋找環境定義的命令
 環境命令是在 .vsct 檔案的集合中定義的：

- SharedCmdDef. .vsct

- SharedCmdPlace. .vsct

- ShellCmdDef. .vsct

- ShellCmdPlace. .vsct

  這些檔案位於 *\<Visual STUDIO SDK 安裝路徑 >* \VisualStudioIntegration\Common\Inc \\。 這些檔案會提供功能表和群組的定義和 Guid，您可以在 VSPackage 的命令資料表設定（. .vsct）檔案中使用這些功能，做為您自己的功能表、群組和命令的容器。

## <a name="in-this-section"></a>本章節內容
- [Visual Studio 功能表的 GUID 和 ID](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 提供 Visual Studio 功能表列上功能表的 GUID 和識別碼值，以及其所包含的群組。

- [Visual Studio 工具列的 GUID 和 ID](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 提供 Visual Studio IDE 中工具列和其所包含之群組的 GUID 和識別碼值。

- [Visual Studio 命令的 GUID 和 ID](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 提供 Visual Studio IDE 所定義之命令的 GUID 和識別碼值。

## <a name="see-also"></a>請參閱
- [Visual Studio 命令表檔案 (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [用來擴充專案系統的 IDE 定義的命令](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [VSPackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)