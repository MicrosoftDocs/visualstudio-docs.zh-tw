---
title: 擴充功能表和命令 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c344d996c70012ef1516fa2bebe52394739bea35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85768586"
---
# <a name="extend-menus-and-commands"></a>擴充功能表和命令
命令是您將動作和進程新增至 Visual Studio 的方式。 在大部分的情況下，命令會顯示在功能表或工具列上。 VSPackage 專案範本會顯示如何執行非常基本的命令。 如果稍微長一點，但仍有基本的執行，請參閱 [使用功能表命令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)模組。

 如需有關 Visual Studio 命令、功能表和工具列的詳細資訊，請參閱 [命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。

 命令、功能表和工具列是在 VSPackage 專案的 *.vsct* 檔案中定義的。 您可以在[vspackage 加入使用者介面元素的方式](../extensibility/internals/how-vspackages-add-user-interface-elements.md)中，找到 Visual Studio IDE 和 *.vsct*檔案的相關資訊。

 下列主題說明如何新增不同類型的命令、功能表和工具列。

## <a name="in-this-section"></a>本節內容
- [將功能表新增至 Visual Studio 的功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) 說明如何將功能表新增至頂端 Visual Studio 的功能表列。

- [將鍵盤快速鍵系結至功能表項目](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) 說明如何將鍵盤快速鍵 (例如 CTRL + 3) 新增至功能表項目。

- [將子功能表新增至功能表](../extensibility/adding-a-submenu-to-a-menu.md) 說明如何將子功能表新增至上方功能表。

- [將最近使用的清單新增至子功能表](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) 說明如何新增最近使用的清單。

- [建立可重複使用的按鈕群組](../extensibility/creating-reusable-groups-of-buttons.md) 描述如何將命令專案分組，讓它們可以包含在多個功能表中。

- [將圖示新增至功能表命令](../extensibility/adding-icons-to-menu-commands.md) 描述如何將圖示新增至工具列和功能表上的命令。

- [變更功能表命令的文字](../extensibility/changing-the-text-of-a-menu-command.md) 描述如何使用旗標 `TextChanges` ，讓功能表項目動態變更。

- [變更命令的外觀](../extensibility/changing-the-appearance-of-a-command.md) 說明如何動態啟用或停用命令。

- [更新使用者介面](../extensibility/updating-the-user-interface.md) 說明如何強制更新使用者介面，以反映最近的變更。

- [當地語系化功能表命令](../extensibility/localizing-menu-commands.md) 說明如何當地語系化功能表命令。
