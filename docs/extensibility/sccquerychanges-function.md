---
title: SccQueryChanges 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 617f07a11f92ab65f079c7d1b41773494e3d0c8b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720859"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges 函式
此函式會列舉指定的檔案清單，並透過回呼函數提供每個檔案的名稱變更相關資訊。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>參數
 pCoNtext

在原始檔控制外掛程式內容指標。

 n

在@No__t_0 陣列中的檔案數目。

 lpFileNames

在要取得相關資訊的檔案名陣列。

 pfnCallback

在要針對清單中的每個檔案名呼叫的回呼函式（如需詳細資訊，請參閱[QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) ）。

 pvCallerData

在將原封不動地傳遞至回呼函式的值。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式執行應會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|查詢程式已順利完成。|
|SCC_E_PROJNOTOPEN|尚未在原始檔控制中開啟專案。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或競爭問題。|
|SCC_E_NONSPECIFICERROR|發生未指定或一般的錯誤。|

## <a name="remarks"></a>備註
 所查詢的變更是命名空間：具體來說，就是重新命名、新增和移除檔案。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [錯誤碼](../extensibility/error-codes.md)