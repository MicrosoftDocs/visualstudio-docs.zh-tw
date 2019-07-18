---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5aefe3b348f36b32792ebce9600f846d5a9cffe
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317835"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
這個方法會取得伺服器的機器的公用程式。

> [!NOTE]
> 這個方法已經過時： 請勿使用 ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]一律會傳回`E_NOTIMPL`如果在呼叫此方法)。 它會保留歷程記錄的原因。

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

## <a name="parameters"></a>參數
`ppUtil`\
[out]傳回`IDebugMDMUtil2_V7`表示機器的公用程式資訊的介面。

## <a name="return-value"></a>傳回值
 一律會傳回`E_NOTIMPL`，指出，該方法尚未實作。

## <a name="remarks"></a>備註
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 一律會傳回`E_NOTIMPL`如果呼叫這個方法。

## <a name="see-also"></a>另請參閱
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)