---
title: IDebugProcess3::獲取可用狀態 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetENCAvailableState
helpviewer_keywords:
- IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77345cfc3aa1dd95482052893e7c09591ad7cd4e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723651"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
此方法獲取進程的當前"編輯並繼續"狀態。 自訂埠供應商應始終傳回`E_NOTIMPL`。

## <a name="syntax"></a>語法

```cpp
HRESULT GetENCAvailableState(
   EncUnavailableReason* pReason
);
```

```csharp
int GetENCAvailableState(
   EncUnavailableReason[] pReason
);
```

## <a name="parameters"></a>參數
`pReason`\
[出][來自 Enc 不可用原因](../../../extensibility/debugger/reference/encunavailablereason.md)枚舉的值。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

> [!NOTE]
> 自訂埠供應商應始終傳回`E_NOTIMPL`。

## <a name="remarks"></a>備註
 此狀態可能受禁用[ENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)的影響。

## <a name="see-also"></a>另請參閱
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
