---
title: 列出執行緒命令
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44c66eab323f42ba3aa5392fed657e3afd3a6e5c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55947012"
---
# <a name="list-threads-command"></a>列出執行緒命令
顯示目前程式中的執行緒清單。

## <a name="syntax"></a>語法

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>引數
 `index`

 選擇性。 依據索引選取一個執行緒，以成為目前執行緒。

## <a name="remarks"></a>備註
 指定時，`index` 引數會將指出的執行緒標記為目前執行緒。 星號 (*) 會顯示在目前執行緒旁邊的清單。

## <a name="example"></a>範例

```
>Debug.ListThreads
```

## <a name="see-also"></a>請參閱

- [列出呼叫堆疊命令](../../ide/reference/list-call-stack-command.md)
- [列出反組譯碼命令](../../ide/reference/list-disassembly-command.md)
- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)