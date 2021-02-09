---
title: SccGetVersion 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 91daeca1df76f6b624d0eddf9d28222369b2cc4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844537"
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

|WORD|Description|
|----------|-----------------|
|HIWORD|主要版本|
|LOWORD|次要版本|

## <a name="remarks"></a>備註
 例如，如果原始檔控制外掛程式支援版本1.3 的原始檔控制外掛程式 API，則此函式會傳回0x0103。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
