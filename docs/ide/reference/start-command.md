---
title: Start 命令
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6138c4cff33f0b2a4211439a01a058da59da811
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590276"
---
# <a name="start-command"></a>Start 命令
開始偵錯啟始專案。

## <a name="syntax"></a>語法

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>引數
`address`

選擇性。 程式暫停執行的位址，與原始程式碼中的中斷點類似。 此引數只適用於偵錯模式。

## <a name="remarks"></a>備註
**Start** 命令在執行時，會對指定的位址執行 RunToCursor 運算。

## <a name="example"></a>範例
此範例會啟動偵錯工具，並忽略任何發生的例外狀況。

```cmd
>Debug.Start
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [視覺化工作室命令別名](../../ide/reference/visual-studio-command-aliases.md)
