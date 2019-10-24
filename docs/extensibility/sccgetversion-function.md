---
title: SccGetVersion 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69078200743f30c4ecfedce8e9be05ef9e7ce20b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721474"
---
# <a name="sccgetversion-function"></a>SccGetVersion 函式
此函式會取得原始檔控制外掛程式支援的原始檔控制外掛程式 API 版本號碼。

## <a name="syntax"></a>語法

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>參數
 無。

## <a name="return-value"></a>傳回值
 @No__t_0 資料類型，其中包含支援的原始檔控制外掛程式 API 的版本號碼：

|WORD|描述|
|----------|-----------------|
|HIWORD|主要版本|
|LOWORD|次要版本|

## <a name="remarks"></a>備註
 例如，如果原始檔控制外掛程式支援原始檔控制外掛程式 API 的1.3 版，則此函式會傳回0x0103。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)