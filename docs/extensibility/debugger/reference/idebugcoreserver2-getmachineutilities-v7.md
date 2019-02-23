---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b7b0aa54cb5102867ba536729404ad298db9fd3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678172"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
這個方法會取得伺服器的機器的公用程式。

> [!NOTE]
>  這個方法已經過時： 請勿使用 ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]一律會傳回`E_NOTIMPL`如果在呼叫此方法)。 它會保留歷程記錄的原因。

## <a name="syntax"></a>語法

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

#### <a name="parameters"></a>參數
 `ppUtil`

 [out]傳回`IDebugMDMUtil2_V7`表示機器的公用程式資訊的介面。

## <a name="return-value"></a>傳回值
 一律會傳回`E_NOTIMPL`，指出，該方法尚未實作。

## <a name="remarks"></a>備註
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 一律會傳回`E_NOTIMPL`如果呼叫這個方法。

## <a name="see-also"></a>另請參閱
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)