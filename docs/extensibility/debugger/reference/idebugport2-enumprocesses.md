---
title: IDebugPort2::EnumProcesses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::EnumProcesses
helpviewer_keywords:
- IDebugPort2::EnumProcesses
ms.assetid: aafb32c5-5790-4807-a448-878a80256438
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5c1b5b43007e43a5cee368622d808d20ad5b83b5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343805"
---
# <a name="idebugport2enumprocesses"></a>IDebugPort2::EnumProcesses
傳回一份連接埠上執行的所有處理程序。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumProcesses( 
   IEnumDebugProcesses2** ppEnum
);
```

```csharp
int EnumProcesses( 
   out IEnumDebugProcesses2 ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
[out]傳回[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)物件，其中包含一份連接埠上執行的所有處理程序。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)