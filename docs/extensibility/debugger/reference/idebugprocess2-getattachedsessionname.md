---
description: 取得正在對此進程進行偵錯工具的會話名稱。
title: IDebugProcess2：： GetAttachedSessionName |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 426904f777d65a25b92871767649cb26041e2af8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071541"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
取得正在對此進程進行偵錯工具的會話名稱。 IDE 可以將這項資訊顯示給正在將特定電腦上的特定進程進行偵錯工具的使用者。

> [!NOTE]
> 這個方法已被取代，而且其實應一律傳回 `E_NOTIMPL` 。

## <a name="syntax"></a>語法

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

## <a name="parameters"></a>參數
`pbstrSessionName`\

## <a name="return-value"></a>傳回值
 這個方法應該一律傳回 `E_NOTIMPL` 。

## <a name="see-also"></a>另請參閱
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
