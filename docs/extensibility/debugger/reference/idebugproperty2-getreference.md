---
title: IDebug屬性2::獲取參考 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetReference
helpviewer_keywords:
- IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4f119a00139e2af44f771fa0903c73b8003dd77f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721352"
---
# <a name="idebugproperty2getreference"></a>IDebugProperty2::GetReference
返回對屬性值的引用。

## <a name="syntax"></a>語法

```cpp
HRESULT GetReference(
   IDebugReference2** ppReference
);
```

```csharp
int GetReference(
   out IDebugReference2 ppReference
);
```

## <a name="parameters"></a>參數
`ppRererence`\
[出]返回表示對屬性值的引用的[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,傳回錯誤代碼(`E_NOTIMPL`通常`E_GETREFERENCE_NO_REFERENCE`或 。

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
