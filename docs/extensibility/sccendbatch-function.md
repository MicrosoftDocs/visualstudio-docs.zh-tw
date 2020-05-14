---
title: SccEndBatch 功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51fe7e0bc0d417ffa182fbc68fd2779ed0b625d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700915"
---
# <a name="sccendbatch-function"></a>SccEndBatch 功能
此功能完成一批原始程式碼管理操作。 這些批次可能無法嵌套。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>參數
 無。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|一批操作成功結束。|
|SCC_E_UNKNOWNERROR|非特異性故障。|

## <a name="remarks"></a>備註
 原始程式碼管理批次處理用於跨多個專案或多個上下文執行相同的原始程式碼管理操作。 批次處理可用於在批次處理操作期間從用戶體驗中消除冗餘對話框。 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)`SccEndBatch`和 函數用作一對,以指示操作的開始和結束。 它們不能嵌套。

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 功能](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
