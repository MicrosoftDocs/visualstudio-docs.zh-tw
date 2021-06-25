---
description: 此函式會取得原始檔控制外掛程式所支援的原始檔控制外掛程式 API 版本號碼。
title: SccGetVersion 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f49d33ebe70390a364d0ae8336e7f69549b6876f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901080"
---
# <a name="sccgetversion-function"></a>SccGetVersion 函式
此函式會取得原始檔控制外掛程式所支援的原始檔控制外掛程式 API 版本號碼。

## <a name="syntax"></a>語法

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>參數
 無。

## <a name="return-value"></a>傳回值
 `LONG`資料類型，包含支援的原始檔控制外掛程式 API 的版本號碼：

|WORD|描述|
|----------|-----------------|
|HIWORD|主要版本|
|LOWORD|次要版本|

## <a name="remarks"></a>備註
 例如，如果原始檔控制外掛程式支援版本1.3 的原始檔控制外掛程式 API，則此函式會傳回0x0103。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
