---
title: IEnumDebugPropertyInfo2::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2::Reset
helpviewer_keywords:
- IEnumDebugPropertyInfo2::Reset
ms.assetid: fa4201c1-4633-4596-93aa-bd415c4ed71a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d8cf8af9b8d042748bf37f90d059a97d06f1c77
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704289"
---
# <a name="ienumdebugpropertyinfo2reset"></a>IEnumDebugPropertyInfo2::Reset
將列舉重設第一個項目。

## <a name="syntax"></a>語法

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 呼叫這個方法是，下一個呼叫之後[下一步](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)方法會傳回第一個元素的列舉型別。

## <a name="see-also"></a>另請參閱
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)