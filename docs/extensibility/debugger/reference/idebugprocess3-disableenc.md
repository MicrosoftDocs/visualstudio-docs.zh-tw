---
title: IDebugProcess3::D可微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b39bb448501bacd5ab458b7e61bb1a5044bc8a3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723728"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
此方法顯式禁用此過程上的「編輯並繼續」(以及它包含的所有程式)。 自訂埠供應商應始終傳回`E_NOTIMPL`。

## <a name="syntax"></a>語法

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>參數
`reason`\
[在][來自 Enc 不可用原因](../../../extensibility/debugger/reference/encunavailablereason.md)枚舉的值。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

> [!NOTE]
> 自訂埠供應商應始終傳回`E_NOTIMPL`。

## <a name="remarks"></a>備註
 一旦進程禁用了"編輯並繼續",只能通過重新啟動進程重新啟用它。

## <a name="see-also"></a>另請參閱
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
