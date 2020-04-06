---
title: SccClose專案功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71df385bc0cf42c2437abfd117c2f84bda5b5432
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701053"
---
# <a name="scccloseproject-function"></a>SccClose 專案功能
此函數關閉項目,標誌著特定會話的結束。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>參數
 pvContext 原始程式碼管理外掛程式上下文結構。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|專案已成功關閉。|
|SCC_E_PROJNOTOPEN|當前未打開任何專案。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行此操作。|
|SCC_E_NONSPECIFICERROR|非特異性故障。|

## <a name="remarks"></a>備註
 在此函數之前始終調用[SccOpenProject。](../extensibility/sccopenproject-function.md) 然後調用此函數後,調用`SccOpenProject`函數或[SccUn 初始化](../extensibility/sccuninitialize-function.md),從而完全結束與原始程式碼管理系統的連接。

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 功能](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
