---
title: IDebug位址:獲取位址 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 162a64c9118bdcde23208082350005e607a237b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736601"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
返回描述物件及其在其範圍或容器中的位置的結構。

## <a name="syntax"></a>語法

```cpp
HRESULT GetAddress (
   DEBUG_ADDRESS * pAddress
);
```

```csharp
int GetAddress(
   DEBUG_ADDRESS[] pAddress
);
```

## <a name="parameters"></a>參數
`pAddress`\
[進出]由此方法填充[DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構傳遞給此方法,然後使用適當的資訊填充它。 如何解釋此資訊取決於返回的資訊類型和符號處理程式本身。 有關詳細資訊,請參閱[DEBUG_ADDRESS。](../../../extensibility/debugger/reference/debug-address.md)

## <a name="see-also"></a>另請參閱
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
