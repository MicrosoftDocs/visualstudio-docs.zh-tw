---
title: SetNotificationForWaitCompletion 方法 |Microsoft Docs
description: 瞭解偵錯工具如何使用狀態位，協助跳出非承諾樣式工作的非同步方法主體。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2418e958c027fea7fd39c93b0d5abbd95d64435b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960788"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion 方法
設定或清除 TASK_STATE_WAIT_COMPLETION_NOTIFICATION 狀態位。

 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>

 **元件：** *mscorlib.dll*) 中的 mscorlib (

## <a name="syntax"></a>語法

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>參數
 `enabled`

 `true` 設定位;取消設定 `false` 位。

## <a name="exceptions"></a>例外

## <a name="remarks"></a>備註
 偵錯工具會設定此位，以協助跳出非同步方法主體。 如果 `enabled` 為 `true` ，則必須在尚未完成的工作上呼叫這個方法。 當 `enabled` 為時 `false` ，可以在已完成的工作上呼叫這個方法。 在任一事件中，它只能用於承諾樣式的工作。

## <a name="requirements"></a>規格需求

## <a name="see-also"></a>另請參閱
- [Task 類別](../../extensibility/debugger/task-class-internal-members.md)
