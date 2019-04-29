---
title: IDebugPortSupplier2::GetPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::GetPort
helpviewer_keywords:
- IDebugPortSupplier2::GetPort
ms.assetid: d55d5055-7386-4037-bf22-4c3e434a99ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65b2d8264ef75c46de32ee65d994794d526c7ddb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871418"
---
# <a name="idebugportsupplier2getport"></a>IDebugPortSupplier2::GetPort
從連接埠提供者取得的連接埠。

## <a name="syntax"></a>語法

```cpp
HRESULT GetPort( 
   REFGUID       guidPort,
   IDebugPort2** ppPort
);
```

```csharp
int GetPort( 
   ref Guid        guidPort,
   out IDebugPort2 ppPort
);
```

#### <a name="parameters"></a>參數
 `guidPort`

 [in]連接埠的全域唯一識別碼 (GUID)。

 `ppPort`

 [out]傳回[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)物件，表示連接埠。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。 傳回`E_PORTSUPPLIER_NO_PORT`如果沒有連接埠存在具有指定識別項。

## <a name="see-also"></a>另請參閱
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)