---
title: 列出執行緒命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc11479901785b19235e0962d3ae90e552e5b33b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671145"
---
# <a name="list-threads-command"></a>列出執行緒命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

顯示目前程式中的執行緒清單。

## <a name="syntax"></a>語法

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>引數
 `index` 選擇項。 依據索引選取一個執行緒，以成為目前執行緒。

## <a name="remarks"></a>備註
 指定時，`index` 引數會將指出的執行緒標記為目前執行緒。 星號 (*) 會顯示在目前執行緒旁邊的清單。

## <a name="example"></a>範例

```
>Debug.ListThreads
```

## <a name="see-also"></a>另請參閱
 [列出呼叫堆疊命令](../../ide/reference/list-call-stack-command.md)[清單反組解碼命令](../../ide/reference/list-disassembly-command.md) [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)[命令視窗](../../ide/reference/command-window.md)[尋找/命令框](../../ide/find-command-box.md) [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
