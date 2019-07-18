---
title: IDebugProcess2::Detach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3948ecce15b9b2b2e8b3bf974ecc2277d9fa0360
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353191"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
會從這個處理序偵錯工具中斷連結所有處理序中的程式中斷連結。

## <a name="syntax"></a>語法

```cpp
HRESULT Detach( 
   void 
);
```

```csharp
int Detach();
```

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 所有程式和處理程序繼續執行，但不會再偵錯工作階段的一部分。 卸離作業之後完成，沒有更多偵錯此處理程序 （和其程式） 的事件將會傳送。

## <a name="see-also"></a>另請參閱
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)