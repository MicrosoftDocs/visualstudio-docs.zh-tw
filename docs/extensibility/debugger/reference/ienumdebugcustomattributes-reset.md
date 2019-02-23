---
title: IEnumDebugCustomAttributes::Reset |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Reset
helpviewer_keywords:
- IEnumDebugCustomAttributes::Reset
ms.assetid: e0db6518-5a71-4adb-a407-4d2ac7a3e369
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c25d2dc63002d41d49e6bdac8a106217ff49e277
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719661"
---
# <a name="ienumdebugcustomattributesreset"></a>IEnumDebugCustomAttributes::Reset
將列舉序列重設為開頭。

## <a name="syntax"></a>語法

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 呼叫這個方法是，下一個呼叫之後[下一步](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)方法會傳回第一個元素的列舉型別。

## <a name="see-also"></a>另請參閱
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
- [下一步](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)