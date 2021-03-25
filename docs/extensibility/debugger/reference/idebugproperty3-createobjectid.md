---
description: 建立這個屬性的唯一識別碼，以確保它在所有其他屬性中都是唯一的。
title: IDebugProperty3：： CreateObjectID |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af90f360e59e04cc5d55017c5d986e6682bab2ed
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064809"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
建立這個屬性的唯一識別碼，以確保它在所有其他屬性中都是唯一的。

## <a name="syntax"></a>語法

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 當會話偵錯工具管理員想要確保在所有其他屬性中唯一識別這個屬性時，會呼叫這個方法。 除非已唯一識別它所處理的屬性，否則 debug engine (DE) 支援此方法。 如果 DE 不支援這個方法，則會傳回 `E_NOTIMPL` 。

 在 `CreateObjectID` 呼叫 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) 方法時，會終結以建立的任何唯一識別碼，這也表示需要唯一識別此屬性的結尾。

> [!NOTE]
> 沒有任何方法可以取出這個唯一的識別碼，因此當呼叫方法時，DE 可以執行任何想要的唯一識別碼 `CreateObjectID` 。

## <a name="see-also"></a>另請參閱
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
