---
title: Debug.Print
description: 瞭解 Print 命令，以及它如何評估運算式或顯示指定的文字。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0524ce015ea4675254615c11e5768e59049c37f6
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304131"
---
# <a name="print-command"></a>Print 命令

評估運算式，或顯示指定的文字。

## <a name="syntax"></a>語法

```cmd
>Debug.Print text
```

## <a name="arguments"></a>引數

`text`

必要。 要評估的運算式或要顯示的文字。

## <a name="remarks"></a>備註

您可以使用問號 (?) 作為此命令的別名。 因此；例如，命令

```cmd
>Debug.Print expA
```

也可以寫成

```cmd
? expA
```

這兩個版本的命令都會傳回 `expA` 運算式的目前值。

## <a name="example"></a>範例

```cmd
>Debug.Print DateTime.Now.Day
```

## <a name="see-also"></a>另請參閱

- [評估語句命令](../../ide/reference/evaluate-statement-command.md)
- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
