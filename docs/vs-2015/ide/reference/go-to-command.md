---
title: 移至命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 454b51b6939a78cdaab8d29f51d30910024adbe3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661208"
---
# <a name="go-to-command"></a>移至命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

將游標移至指定的程式行。

## <a name="syntax"></a>語法

```
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>引數
 `linenumber` 選擇項。 整數，代表要移至的行號。

## <a name="remarks"></a>備註
 行編號是從一開始。 如果 `linenumber` 的值小於一，則會顯示第一行。 如果 `linenumber` 的值大於最後一行的行號，則會顯示最後一行。

 如果未指定 `linenumber` 的值，則會顯示 [移至指定行]  對話方塊。

 此命令的別名是 GoToLn。

## <a name="example"></a>範例

```
>Edit.GoTo 125
```

## <a name="see-also"></a>另請參閱
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)[命令視窗](../../ide/reference/command-window.md)[尋找/命令框](../../ide/find-command-box.md) [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
