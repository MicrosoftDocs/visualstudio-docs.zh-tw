---
title: "擴充的功能表和命令 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: "49"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 815aac693686dc59d6934b00fb456c3a1afce72c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="extending-menus-and-commands"></a>擴充的功能表和命令
命令會將動作和處理程序加入至 Visual Studio 的方式。 在大部分情況下會顯示功能表或工具列上的命令。 VSPackage 專案範本會示範如何實作非常基本的命令。 比較麻煩但仍然有基本的實作，請參閱[建立擴充的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
 如需有關 Visual Studio 命令、 功能表和工具列的詳細資訊，請參閱[命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
 VSPackage 專案一部分的.vsct 檔案中定義命令、 功能表和工具列。 您可以找到有關 Visual Studio IDE 和.vsct 檔案中的資訊[如何 Vspackage 加入使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)。  
  
 下列主題說明如何加入不同類型的命令、 功能表和工具列。  
  
## <a name="in-this-section"></a>本節內容  
 [將功能表加入至 Visual Studio 功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 說明如何將功能表加入 Visual Studio 功能表列上方。  
  
 [將鍵盤快速鍵繫結至功能表項目](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 說明如何將鍵盤快速鍵 （例如 CTRL + 3） 加入至功能表項目。  
  
 [將子功能表加入至功能表](../extensibility/adding-a-submenu-to-a-menu.md)  
 說明如何將子功能表新增至上方的功能表。  
  
 [將最近使用的清單新增至子功能表](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 說明如何加入 最近使用的清單。  
  
 [建立可重複使用的按鈕群組](../extensibility/creating-reusable-groups-of-buttons.md)  
 描述如何分組，讓它們可以包含多個功能表上的命令項目。  
  
 [將圖示加入至功能表命令](../extensibility/adding-icons-to-menu-commands.md)  
 描述如何將圖示加入至工具列和功能表上的命令。  
  
 [變更功能表命令的文字](../extensibility/changing-the-text-of-a-menu-command.md)  
 說明如何使用`TextChanges`旗標來啟用動態變更功能表項目。  
  
 [變更命令的外觀](../extensibility/changing-the-appearance-of-a-command.md)  
 描述如何以動態方式啟用或停用命令。  
  
 [更新使用者介面](../extensibility/updating-the-user-interface.md)  
 描述如何強制更新的使用者介面，以反映最近的變更。  
  
 [將功能表命令當地語系化](../extensibility/localizing-menu-commands.md)  
 說明如何以當地語系化功能表命令。  
  
## <a name="related-sections"></a>相關章節