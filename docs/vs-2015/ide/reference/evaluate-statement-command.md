---
title: 評估陳述式命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e2db8596c1c16f5c9fb54a8c7c867b06e997b7b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657714"
---
# <a name="evaluate-statement-command"></a>評估陳述式命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

評估並顯示指定的陳述式。

## <a name="syntax"></a>語法

```
Debug.EvaluateStatement text
```

## <a name="arguments"></a>引數
 需要 `text`。 要評估的陳述式。

## <a name="remarks"></a>備註
 用來輸入 **EvaluateStatement** 命令的視窗可判斷是否將等號 (=) 解譯為比較運算子或指派運算子。

 在 [命令]**** 視窗中，等號 (=) 會解譯為比較運算子。 因此；例如，如果 `a` 和 `b` 變數的值不同，則命令

```
>Debug.EvaluateStatement(a=b)
```

 會傳回值 `false`。

 相較之下，在 [即時運算]**** 視窗中，等號 (=) 會解譯為指派運算子。 因此；例如，命令

```
>Debug.EvaluateStatement(a=b)
```

 會將 `b` 變數的值指派給變數 `a`。

## <a name="example"></a>範例

```
>Debug.EvaluateStatement(a+b)
```

## <a name="see-also"></a>另請參閱
 [列印命令](../../ide/reference/print-command.md) [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)[視窗](../../ide/reference/command-window.md)[尋找/命令框](../../ide/find-command-box.md) [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
