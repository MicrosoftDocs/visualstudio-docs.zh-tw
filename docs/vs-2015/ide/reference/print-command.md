---
title: 列印命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 136edf7fa91e4caeb9303edfd4441ee178fa6038
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662148"
---
# <a name="print-command"></a>列印命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

評估運算式，或顯示指定的文字。

## <a name="syntax"></a>語法

```
Debug.Print text
```

## <a name="arguments"></a>引數
 需要 `text`。 要評估的運算式或要顯示的文字。

## <a name="remarks"></a>備註
 您可以使用問號 (?) 作為此命令的別名。 因此；例如，命令

```
>Debug.Print expA
```

 也可以寫成

```
>? expA
```

 此命令的兩個版本都會傳回 `expA` 運算式的目前值。

## <a name="example"></a>範例

```
>Debug.Print varA
```

## <a name="see-also"></a>另請參閱
 [評估語句命令](../../ide/reference/evaluate-statement-command.md) [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)[命令視窗](../../ide/reference/command-window.md)[尋找/命令](../../ide/find-command-box.md)方塊[Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
