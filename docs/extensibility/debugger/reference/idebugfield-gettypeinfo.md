---
title: IDebugField:獲取類型資訊 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: faa3464f0396999f36604aa88c429235d4849688
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728774"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
此方法獲取有關符號或類型的資訊與類型無關。

## <a name="syntax"></a>語法

```cpp
HRESULT GetTypeInfo( 
   TYPE_INFO* pTypeInfo
);
```

```csharp
int GetTypeInfo(
   TYPE_INFO[] pTypeInfo
);
```

## <a name="parameters"></a>參數
`pTypeInfo`\
[出]返回提供的[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)結構中的類型資訊。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 與類型無關的資訊將包括 AppDomain、模組和包含符號的類。

## <a name="see-also"></a>另請參閱
- [取得類型](../../../extensibility/debugger/reference/idebugfield-gettype.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
