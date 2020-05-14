---
title: IDebugEvent2::獲取屬性 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ffc3fc1b7988401611190fdf09e8041bf0dc5b1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729951"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
獲取此調試事件的屬性。

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
[出][事件屬性](../../../extensibility/debugger/reference/eventattributes.md)枚舉中標誌的組合。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面是所有事件所共有的。 此方法描述事件的類型;例如,事件是同步事件或異步事件,它是停止事件。

## <a name="see-also"></a>另請參閱
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
