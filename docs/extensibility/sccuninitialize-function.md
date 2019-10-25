---
title: SccUninitialize 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 321f50173e3c1517cc6a431ff74933e1a02ef1d0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720123"
---
# <a name="sccuninitialize-function"></a>SccUninitialize 函式
此函式會清除先前呼叫[SccInitialize](../extensibility/sccinitialize-function.md)所建立的任何配置或開啟的連接，以準備關閉原始檔控制外掛程式。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>參數
 pvCoNtext

在在[SccInitialize](../extensibility/sccinitialize-function.md)中建立之原始檔控制外掛程式內容結構的指標。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式執行應會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|清理已順利完成。|

## <a name="remarks"></a>備註
 原始檔控制外掛程式負責準備要關閉的功能，以及釋放外掛程式已配置給內容結構的記憶體。 函式會針對外掛程式的每個指定實例呼叫一次。 呼叫[SccInitialize](../extensibility/sccinitialize-function.md)在此呼叫之前。 呼叫 `SccUninitialize` 時，仍無法開啟任何專案。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)