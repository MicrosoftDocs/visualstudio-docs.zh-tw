---
title: 切換中斷點命令
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 214897a0f938d8ea52306b8f605948b38f196111
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970461"
---
# <a name="toggle-breakpoint-command"></a>切換中斷點命令
根據中斷點目前的狀態以及在檔案中的目前位置，將其開啟或關閉。

## <a name="syntax"></a>語法

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>引數
 `text` 選擇項。 如果指定文字，則會將行標示為具名中斷點。 否則，行會標示為未命名中斷點，其與按 F9 時所發生的作業類似。

## <a name="example"></a>範例
 下列範例會切換目前中斷點。

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)