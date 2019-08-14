---
title: Watch 命令
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ac779dc902a331a45b600113a11db5364293f74
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925941"
---
# <a name="watch-command"></a>Watch 命令
建立並開啟 [監看式]  視窗的指定執行個體。 您可以使用 [監看式]  視窗來計算變數、運算式和暫存器的值，以編輯這些值，以及儲存結果。

## <a name="syntax"></a>語法

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>引數

`index`\
必要項。 監看式視窗的執行個體數目。

## <a name="remarks"></a>備註

`index` 必須是整數。 有效值為 1、2、3 或 4。

## <a name="example"></a>範例

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>另請參閱

- [[自動變數] 和 [區域變數] 視窗](../../debugger/autos-and-locals-windows.md)
- [在 Visual Studio 中使用監看式及快速監看式視窗在變數設定監看式](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)