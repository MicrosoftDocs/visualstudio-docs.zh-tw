---
title: Debug.Print
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d6f0520d723dab088564e4f97e9ce47a8147db3d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655763"
---
# <a name="print-command"></a>Print 命令

評估運算式，或顯示指定的文字。

## <a name="syntax"></a>語法

```cmd
>Debug.Print text
```

## <a name="arguments"></a>引數

`text`

必要項。 要評估的運算式或要顯示的文字。

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

## <a name="see-also"></a>請參閱

- [評估陳述式命令](../../ide/reference/evaluate-statement-command.md)
- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)