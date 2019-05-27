---
title: IDebugProgram2::GetENCUpdate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 363018d13cfeee1691881f4d8b814cdd0b2dfa35
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212344"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
這個方法會取得此程式的 編輯後繼續 (ENC) 更新。 自訂的偵錯引擎一律會傳回`E_NOTIMPL`。

## <a name="syntax"></a>語法

```cpp
HRESULT GetENCUpdate( 
   IUnknown** ppUpdate
);
```

```csharp
int GetENCUpdate(
   out object ppUpdate
);
```

## <a name="parameters"></a>參數
`ppUpdate`\
[out]傳回可用來更新此程式的內部介面。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

> [!NOTE]
> 自訂的偵錯引擎應該一律傳回`E_NOTIMPL`。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)