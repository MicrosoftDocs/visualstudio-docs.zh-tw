---
title: 切換中斷點命令
description: 瞭解如何使用切換中斷點命令，根據目前的狀態在檔案中的目前位置，開啟或關閉中斷點。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b65144271f91d518dd6649fa1e97fc627d1b0009
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560963"
---
# <a name="toggle-breakpoint-command"></a>切換中斷點命令
根據中斷點目前的狀態以及在檔案中的目前位置，將其開啟或關閉。

## <a name="syntax"></a>語法

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>引數

`text`\
選擇性。 如果指定文字，則會將行標示為具名中斷點。 否則，行會標示為未命名中斷點，其與按 F9 時所發生的作業類似。

## <a name="example"></a>範例
下列範例會切換目前中斷點。

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
