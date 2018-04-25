---
title: IDE 定義命令、 功能表和群組 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b65266ad3367df5cebeabc251bc8bceb6cda7075
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE 定義命令、 功能表和群組
許多的功能表、 命令和命令群組已經定義以供[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。 當您擴充時，還有可供您使用這些命令[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="finding-environment-defined-commands"></a>尋找環境定義的命令  
 一組的四個.vsct 檔案中定義環境命令：  
  
-   SharedCmdDef.vsct  
  
-   SharedCmdPlace.vsct  
  
-   ShellCmdDef.vsct  
  
-   ShellCmdPlace.vsct  
  
 這些檔案位於 *\<Visual Studio SDK 安裝路徑 >* \VisualStudioIntegration\Common\Inc\\。 這些檔案會提供定義和功能表和群組，您可以使用 VSPackage 的命令表 (.vsct) 組態檔中做為容器您自己的功能表、 群組和命令的 Guid。  
  
## <a name="in-this-section"></a>本節內容  
 [Visual Studio 功能表的 GUID 和 ID](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 提供 Visual Studio 功能表列上的功能表和它們所包含的群組的 GUID 和 ID 值。  
  
 [Visual Studio 工具列的 GUID 和 ID](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 提供 Visual Studio IDE 中的工具列和它們所包含的群組的 GUID 和 ID 值。  
  
 [Visual Studio 命令的 GUID 和 ID](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 提供的 GUID 和 ID 值的 Visual Studio IDE 所定義的命令。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表 (。Vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [IDE 定義的命令，以擴充專案系統](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [VSPackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)