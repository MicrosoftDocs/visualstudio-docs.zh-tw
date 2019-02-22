---
title: 設定目前堆疊框架命令
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9eea69dc4d2931f66d4c6769667e23bdfb4eecf1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938279"
---
# <a name="set-current-stack-frame-command"></a>設定目前堆疊框架命令
可讓您設定特定堆疊框架。

## <a name="syntax"></a>語法

```cmd
Debug.SetCurrentStackFrame index
```

## <a name="arguments"></a>引數
 `index`

 必要項。 依索引選取堆疊框架。

## <a name="example"></a>範例

```cmd
>Debug.SetCurrentStackFrame 1
```

## <a name="see-also"></a>請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)