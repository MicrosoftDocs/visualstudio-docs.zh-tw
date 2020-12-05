---
title: NotifyDebuggerOfWaitCompletion 方法 |Microsoft Docs
description: 瞭解 NotifyDebuggerOfWaitCompletion 方法，這是偵錯工具用來作為中斷點目標的預留位置。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 35571b28287ecdea48a2ff089cb25cf3ed742d60
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606628"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion 方法
偵錯工具用來當做中斷點目標的預留位置方法。 這個方法不得內嵌或優化。

 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>

 **元件：** *mscorlib.dll*) 中的 mscorlib (

## <a name="syntax"></a>語法

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>備註
 如果已設定偵錯工具通知位，則所有具有工作的聯結作業都應該呼叫這個方法。

## <a name="requirements"></a>規格需求

## <a name="see-also"></a>另請參閱
- [Task 類別](../../extensibility/debugger/task-class-internal-members.md)
