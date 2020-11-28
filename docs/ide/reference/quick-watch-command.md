---
title: 快速監看式命令
description: 深入瞭解 [快速監看式] 命令，以及它如何在 [快速監看式] 視窗的 [運算式] 欄位中顯示所選或指定的文字。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6185418364e8b22e1f473308b2db9899c8778d13
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304166"
---
# <a name="quick-watch-command"></a>快速監看式命令
可顯示[快速監看式](../../debugger/watch-and-quickwatch-windows.md)視窗的 [運算式] 欄位中所選取或指定的文字。 您可以使用此對話方塊來計算偵錯工具辨識的變數或運算式目前的值，或暫存器的內容。 此外，您可以變更任何非 const 變數的值或任何暫存器的內容。

## <a name="syntax"></a>語法

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>引數

`text`\
選擇性。 要新增至 [快速監看式] 對話方塊的文字。

## <a name="remarks"></a>備註

如果省略 `text`，則會將游標處目前選取的文字或字組新增至監看式視窗。

## <a name="example"></a>範例

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中使用監看式及快速監看式視窗在變數設定監看式](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
