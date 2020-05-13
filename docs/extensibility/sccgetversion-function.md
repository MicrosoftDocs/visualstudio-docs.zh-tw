---
title: SccGet 版本功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a563a7d1d65dc4c6564abd4e337242eea1aa9924
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700668"
---
# <a name="sccgetversion-function"></a>SccGetVersion 函式
此功能獲取原始程式碼管理外掛程式支援的原始程式碼管理外掛程式 API 的版本號。

## <a name="syntax"></a>語法

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>參數
 無。

## <a name="return-value"></a>傳回值
 包含`LONG`支援的原始碼管理外掛程式 API 的版本號的資料型態:

|WORD|描述|
|----------|-----------------|
|希WORD|主要版本|
|洛沃|次要版本|

## <a name="remarks"></a>備註
 例如,如果原始程式碼管理外掛程式支援原始程式碼管理外掛程式 API 的版本 1.3,則此功能將傳回 0x0103。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
