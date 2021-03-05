---
description: 取得這個 debug 事件的屬性。
title: IDebugEvent2：： GetAttributes |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7402c2b5a367a3a0a681a9a17ef89872a7b3e96
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152971"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
取得這個 debug 事件的屬性。

## <a name="syntax"></a>語法

```cpp
HRESULT GetAttribute( 
   DWORD* pdwAttrib
);
```

```csharp
int GetAttribute( 
   out uint pdwAttrib
);
```

## <a name="parameters"></a>參數
`pdwAttrib`\
擴展 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) 列舉中的旗標組合。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面通用於所有事件。 這個方法會描述事件的類型;例如，事件是同步或非同步，而是停止事件。

## <a name="see-also"></a>另請參閱
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
