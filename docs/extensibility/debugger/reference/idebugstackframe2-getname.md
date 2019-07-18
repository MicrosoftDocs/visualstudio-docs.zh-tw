---
title: IDebugStackFrame2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetName
helpviewer_keywords:
- IDebugStackFrame2::GetName
ms.assetid: 069d4f96-363f-404e-9c89-5318c4c9821b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3d50fc1b711c673d8582be0d1208bc1d56e0f38b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352110"
---
# <a name="idebugstackframe2getname"></a>IDebugStackFrame2::GetName
取得堆疊框架的名稱。

## <a name="syntax"></a>語法

```cpp
HRESULT GetName ( 
   BSTR* pbstrName
);
```

```csharp
int GetName ( 
   out string pbstrName
);
```

## <a name="parameters"></a>參數
`pbstrName`\
[out]傳回堆疊框架的名稱。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 堆疊框架的名稱通常是正在執行之方法的名稱。

## <a name="see-also"></a>另請參閱
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)