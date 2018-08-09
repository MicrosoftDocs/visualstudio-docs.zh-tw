---
title: 擴充功能表和命令 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e6f5cd78709c9a4843588188494b4a70f7268742
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639746"
---
# <a name="extend-menus-and-commands"></a>擴充功能表和命令
命令會將動作和程序新增至 Visual Studio 的方式。 在大部分情況下會顯示功能表或工具列上的命令。 VSPackage 專案範本會示範如何實作非常基本的命令。 如需略長，但仍有基本的實作，請參閱[建立具有功能表命令的延伸模組](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
 如需有關 Visual Studio 命令、 功能表和工具列的詳細資訊，請參閱 <<c0> [ 命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
 中所定義的命令、 功能表和工具列 *.vsct*檔案也就是 VSPackage 專案的一部分。 您可以找到有關 Visual Studio IDE 的資訊並 *.vsct*中的檔案[如何 Vspackage 加入使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)。  
  
 下列主題說明如何加入不同類型的命令、 功能表和工具列。  
  
## <a name="in-this-section"></a>本節內容  
 [將功能表加入 Visual Studio 功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 說明如何將 Visual Studio 功能表列頂端的功能表。  
  
 [將鍵盤快速鍵繫結至功能表項目](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 說明如何將鍵盤快速鍵 （例如 CTRL + 3） 新增至功能表項目。  
  
 [將子功能表加入至功能表](../extensibility/adding-a-submenu-to-a-menu.md)  
 說明如何將子功能表加入至頂端的功能表。  
  
 [新增 最近使用的子功能表清單](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 說明如何新增最近使用的清單。  
  
 [建立可重複使用的按鈕群組](../extensibility/creating-reusable-groups-of-buttons.md)  
 描述如何分組命令項目，以便它們能夠包含多個功能表上。  
  
 [將圖示加入至功能表命令](../extensibility/adding-icons-to-menu-commands.md)  
 描述如何將圖示加入至工具列和功能表上的命令。  
  
 [變更功能表命令的文字](../extensibility/changing-the-text-of-a-menu-command.md)  
 說明如何使用`TextChanges`旗標來啟用動態變更功能表項目。  
  
 [變更命令的外觀](../extensibility/changing-the-appearance-of-a-command.md)  
 說明如何以動態方式啟用或停用的命令。  
  
 [更新使用者介面](../extensibility/updating-the-user-interface.md)  
 描述如何強制使用者介面，以反映最新變更的更新。  
  
 [將功能表命令當地語系化](../extensibility/localizing-menu-commands.md)  
 說明如何將功能表命令當地語系化。  