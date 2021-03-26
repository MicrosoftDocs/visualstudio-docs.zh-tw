---
description: 這個方法會明確停用此進程的 [編輯後繼續] (以及它包含) 的所有程式。
title: IDebugProcess3：:D isableENC |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7f9c4a1e05cf7d4a98489daf0c2ee3377d54f417
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081616"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
這個方法會明確停用此進程的 [編輯後繼續] (以及它包含) 的所有程式。 自訂埠供應商應該一律傳回 `E_NOTIMPL` 。

## <a name="syntax"></a>語法

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>參數
`reason`\
在來自 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) 列舉的值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

> [!NOTE]
> 自訂埠供應商應該一律傳回 `E_NOTIMPL` 。

## <a name="remarks"></a>備註
 一旦停用某個進程的 [編輯後繼續]，就只能藉由重新開機處理常式來重新啟用。

## <a name="see-also"></a>另請參閱
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
