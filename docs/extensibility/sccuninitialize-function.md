---
description: 此函式會清除先前呼叫 SccInitialize 所建立的任何配置或開啟的連接，以準備關閉原始檔控制外掛程式。
title: SccUninitialize 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7d387167e2032cbb253e86f8d67da38f99fc1076
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063769"
---
# <a name="sccuninitialize-function"></a>SccUninitialize 函式
此函式會清除先前呼叫 [SccInitialize](../extensibility/sccinitialize-function.md) 所建立的任何配置或開啟的連接，以準備關閉原始檔控制外掛程式。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>參數
 pvCoNtext

在在 [SccInitialize](../extensibility/sccinitialize-function.md)中建立的原始檔控制外掛程式內容結構的指標。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|清除作業已順利完成。|

## <a name="remarks"></a>備註
 原始檔控制外掛程式負責準備關閉，以及釋出外掛程式已配置給內容結構的記憶體。 此函式會針對外掛程式的每一個指定實例呼叫一次。 對 [SccInitialize](../extensibility/sccinitialize-function.md) 的呼叫會在此呼叫之前。 在呼叫時，仍無法開啟任何專案 `SccUninitialize` 。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
