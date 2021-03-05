---
description: 這個方法會取得伺服器的電腦公用程式。
title: IDebugCoreServer2：： GetMachineUtilities_V7 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc58f41d9cca98f6c15c164ed4acb941345627e5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154765"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
這個方法會取得伺服器的電腦公用程式。

> [!NOTE]
> 這個方法已經過時： [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] `E_NOTIMPL` 如果呼叫這個方法) ，請不要使用 (一律會傳回。 基於歷史原因，它會保留下來。

## <a name="syntax"></a>語法

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>參數
`ppUtil`\
擴展傳回 `IDebugMDMUtil2_V7` 表示電腦公用程式資訊的介面。

## <a name="return-value"></a>傳回值
 一律 `E_NOTIMPL` 會傳回，表示不會執行此方法。

## <a name="remarks"></a>備註
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]`E_NOTIMPL`如果呼叫這個方法，一律會傳回。

## <a name="see-also"></a>另請參閱
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
