---
title: 延伸選單和指令 |微軟文件
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
ms.openlocfilehash: dfcedd3f1b4cb48631541f1726556dab766402ab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711805"
---
# <a name="extend-menus-and-commands"></a>延伸選單與指令
命令是向可視化工作室添加操作和進程的方式。 在大多數情況下,命令顯示在菜單或工具列上。 VSPackage 專案範本展示如何實現非常基本的命令。 有關稍長但仍處於基本實現的時間,請參閱[使用功能表命令創建擴展](../extensibility/creating-an-extension-with-a-menu-command.md)。

 有關 Visual Studio 指令、選單和工具列的詳細資訊,請參閱[指令、選單和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。

 命令、功能表和工具列在作為 VSPackage 專案的一部分的 *.vsct*檔案中定義。 您可以在[VS 套件如何添加使用者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)中找到有關 Visual Studio IDE 和 *.vsct*檔案的資訊。

 以下主題說明如何添加不同類型的命令、功能表和工具列。

## <a name="in-this-section"></a>本節內容
- [向視覺工作室選單欄新增選單](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)說明如何向頂部 Visual Studio 功能表欄添加功能表。

- [將鍵盤快捷鍵繫結到選單項目](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)說明如何向功能表項添加鍵盤快捷方式(如 CTRL + 3)。

- [加入選單加入子選單](../extensibility/adding-a-submenu-to-a-menu.md)說明如何向頂部功能表添加子功能表。

- [將最近使用的清單加入子選單](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)說明如何添加最近使用的清單。

- [建立可重用的按鈕群組](../extensibility/creating-reusable-groups-of-buttons.md)描述如何對命令項進行分組,以便它們可以包含在多個功能表上。

- [加入選單指令加入圖示](../extensibility/adding-icons-to-menu-commands.md)描述如何向工具列和功能表上的命令添加圖示。

- [變更選單指令的文字](../extensibility/changing-the-text-of-a-menu-command.md)描述使用`TextChanges`標誌以啟用動態更改功能表項。

- [變更指令的外觀](../extensibility/changing-the-appearance-of-a-command.md)描述如何動態啟用或禁用命令。

- [更新使用者介面](../extensibility/updating-the-user-interface.md)描述如何強制更新用戶介面以反映最近的更改。

- [本地化選單指令](../extensibility/localizing-menu-commands.md)說明如何當地語系化功能表命令。
