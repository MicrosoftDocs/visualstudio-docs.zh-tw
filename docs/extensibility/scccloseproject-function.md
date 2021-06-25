---
description: 此函式會關閉專案，並標示特定會話的結尾。
title: SccCloseProject 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 859b1ddea99e74cc1c1dec999611e50216c3c98a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904691"
---
# <a name="scccloseproject-function"></a>SccCloseProject 函式
此函式會關閉專案，並標示特定會話的結尾。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>參數
 pvCoNtext 原始檔控制外掛程式內容結構。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|專案已成功關閉。|
|SCC_E_PROJNOTOPEN|目前未開啟任何專案。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項操作。|
|SCC_E_NONSPECIFICERROR|模糊失敗。|

## <a name="remarks"></a>備註
 [SccOpenProject](../extensibility/sccopenproject-function.md)一律會在此函式之前呼叫。 接著呼叫這個函式，接著呼叫函式 `SccOpenProject` 或 [SccUninitialize](../extensibility/sccuninitialize-function.md)，以完全結束與原始檔控制系統的連接。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
