---
title: IDebugProcess3::DisableENC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2cc26c9d2dae65d8bab0126be5a62b144ebf42b7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63413290"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
這個方法明確地停用編輯後繼續在此程序 （和它包含的所有程式）。 自訂連接埠供應商應該一律傳回`E_NOTIMPL`。

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

#### <a name="parameters"></a>參數
 `reason`

 [in]值，以從[EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)列舉型別。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`，否則會傳回錯誤碼。

> [!NOTE]
> 自訂連接埠供應商應該一律傳回`E_NOTIMPL`。

## <a name="remarks"></a>備註
 一次編輯後繼續 會停用處理程序，可以只藉由重新啟動處理程序重新啟用。

## <a name="see-also"></a>另請參閱
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)