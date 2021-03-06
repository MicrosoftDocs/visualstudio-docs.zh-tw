---
title: 設定基數命令
description: 瞭解「設定基數」命令，以及它如何設定或傳回用來顯示整數值的數值基底。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 50d0097debbd7e91906202b85e8e9e6dab36a27d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957682"
---
# <a name="set-radix-command"></a>設定基數命令
設定或傳回用來顯示整數值的數值基底。

## <a name="syntax"></a>語法

```cmd
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>引數
`10`、`16`、`hex` 或 `dec`

選擇性。 表示十進位 (10 或 dec) 或十六進位 (16 或 hex)。 如果省略引數，則會傳回目前基數值。

## <a name="example"></a>範例
此範例設定環境以十六進位格式顯示整數值。

```cmd
>Debug.SetRadix hex
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)