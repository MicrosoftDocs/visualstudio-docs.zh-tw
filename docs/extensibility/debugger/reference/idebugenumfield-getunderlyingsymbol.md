---
title: IDebugenum欄位:獲取基礎符號 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords:
- IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 14cac9d3f761e95b821179137f2efc23ef61b91b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730279"
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
此方法返回表示枚舉名稱的[IDebugField。](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="syntax"></a>語法

```cpp
HRESULT GetUnderlyingSymbol(
   IDebugField** ppField
);
```

```csharp
int GetUnderlyingSymbol(
   out IDebugField ppField
);
```

## <a name="parameters"></a>參數
`ppField`\
[出]返回描述此枚舉名稱的[IDebugField。](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 枚舉的名稱還包含枚舉的類型,該枚舉通過使用[Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)綁定綁定綁定到記憶體位置。

## <a name="see-also"></a>另請參閱
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [綁定](../../../extensibility/debugger/reference/idebugbinder-bind.md)
