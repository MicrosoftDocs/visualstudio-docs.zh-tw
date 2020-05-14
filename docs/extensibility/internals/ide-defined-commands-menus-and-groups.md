---
title: IDE 定義的指令、功能表和組 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6557f49b019a6793698dabe852919ec2e9f28cfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707722"
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE 定義的命令、功能表和群組
許多功能表、命令和命令組已定義供[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE使用。 這些命令在擴展[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]時也可用於使用。

## <a name="finding-environment-defined-commands"></a>尋找環境定義的指令
 環境命令由四個 .vsct 檔案組定義:

- 共用 CmdDef.vsct

- 共用 CmdPlace.vsct

- 殼牌CmdDef.vsct

- 殼牌CmdPlace.vsct

  這些文件位於\\*\<視覺工作室 SDK 安裝路徑>*[VisualStudio 集成]公共\Inc。 這些檔案提供選單和群組的定義和 GUID,您可以在 VSPackage 的命令表設定 (.vsct) 檔案中用作您自己的選單、組和命令的容器。

## <a name="in-this-section"></a>本節內容
- [Visual Studio 功能表的 GUID 和識別碼](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 在 Visual Studio 功能表列上提供功能表及其包含的組的 GUID 和 ID 值。

- [Visual Studio 工具列的 GUID 和識別碼](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 提供可視化工作室 IDE 中工具列及其包含組的 GUID 和 ID 值。

- [Visual Studio 命令的 GUID 和識別碼](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 提供視覺化工作室 IDE 定義的命令的 GUID 和 ID 值。

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表檔案 (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [用來擴充專案系統的 IDE 定義的命令](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [VSPackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
