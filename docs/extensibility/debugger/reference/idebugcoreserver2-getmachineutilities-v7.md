---
title: IDebugCoreServer2::GetMachineUtilities_V7 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79eba6889583f1dfa482dab107ad31eaaacdbcc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733147"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
此方法獲取伺服器的計算機實用程式。

> [!NOTE]
> 此方法已過時:不使用[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]( 如果呼叫此`E_NOTIMPL`方法, 則始終返回)。 由於歷史原因,它被保留下來。

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
[出]返回表示`IDebugMDMUtil2_V7`計算機實用程式資訊的介面。

## <a name="return-value"></a>傳回值
 始終返回`E_NOTIMPL`,指示該方法未實現。

## <a name="remarks"></a>備註
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]如果調用`E_NOTIMPL`此方法,則始終返回。

## <a name="see-also"></a>另請參閱
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
