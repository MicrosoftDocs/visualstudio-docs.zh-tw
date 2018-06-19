---
title: 列出暫存器命令
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce91abde91edf989b33c476b042abaf16c685df0
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704898"
---
# <a name="list-registers-command"></a>列出暫存器命令
顯示所選暫存器的值，並讓您修改要顯示的暫存器清單。

## <a name="syntax"></a>語法

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>參數
 /Display [{`register`&#124;`registerGroup`}...]

 顯示所指定 `register` 或 `registerGroup` 的值。 如果未指定 `register` 或 `registerGroup`，則會顯示暫存器的預設清單。 如果未指定參數，則行為是相同的。 例如: 

 `Debug.ListRegisters /Display eax`

 相當於

 `Debug.ListRegisters eax`

 /List

 顯示清單中的所有暫存器群組。

 /Watch [{`register`&#124;`registerGroup`}...]

 將一或多個 `register` 或 `registerGroup` 值新增至清單。

 /Unwatch [{`register`&#124;`registerGroup`}...]

 從清單移除一或多個 `register` 或 `registerGroup` 值。

## <a name="remarks"></a>備註
 別名 `r` 可以用來取代 `Debug.ListRegisters`。

## <a name="example"></a>範例
 這個範例會使用 `Debug.ListRegisters` 別名 `r` 顯示暫存器群組 `Flags` 的值。

```cmd
r /Display Flags
```

## <a name="see-also"></a>請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [偵錯基本概念：暫存器視窗](../../debugger/debugging-basics-registers-window.md)
- [如何：使用暫存器視窗](../../debugger/how-to-use-the-registers-window.md)