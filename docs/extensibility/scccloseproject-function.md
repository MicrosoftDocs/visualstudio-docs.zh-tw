---
title: SccCloseProject 函式 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701053"
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
