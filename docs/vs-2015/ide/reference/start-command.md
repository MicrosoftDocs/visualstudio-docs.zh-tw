---
title: Start 命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a216e053a08662da5da04206c780fb4455e9ec09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663499"
---
# <a name="start-command"></a>Start 命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

開始偵錯啟始專案。

## <a name="syntax"></a>語法

```
Debug.Start [address]
```

## <a name="arguments"></a>引數
 `address` 選擇項。 程式暫停執行的位址，與原始程式碼中的中斷點類似。 此引數只適用於偵錯模式。

## <a name="remarks"></a>備註
 **Start** 命令在執行時，會對指定的位址執行 RunToCursor 運算。

## <a name="example"></a>範例
 此範例會啟動偵錯工具，並忽略任何發生的例外狀況。

```
>Debug.Start
```

## <a name="see-also"></a>另請參閱
 [Visual Studio](../../ide/reference/visual-studio-commands.md)命令[視窗](../../ide/reference/command-window.md)[尋找/命令箱](../../ide/find-command-box.md) [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
