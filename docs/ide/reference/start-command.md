---
title: Start 命令
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c1e5ade7d02882633504ac5615ee751b2533adde
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="start-command"></a>Start 命令
開始偵錯啟始專案。

## <a name="syntax"></a>語法

```
Debug.Start [address]
```

## <a name="arguments"></a>引數
 `address`

 選擇性。 程式暫停執行的位址，與原始程式碼中的中斷點類似。 此引數只適用於偵錯模式。

## <a name="remarks"></a>備註
 **Start** 命令在執行時，會對指定的位址執行 RunToCursor 運算。

## <a name="example"></a>範例
 此範例會啟動偵錯工具，並忽略任何發生的例外狀況。

```
>Debug.Start
```

## <a name="see-also"></a>請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)