---
title: SccEndBatch 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e915a2e0c508e62a8d34d8d8a5b4fdcd734bbf8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353697"
---
# <a name="sccendbatch-function"></a>SccEndBatch 函式
此函式結束時，原始檔控制作業的批次。 這些批次可能不是巢狀。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>參數
 無。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功完成的作業批次。|
|SCC_E_UNKNOWNERROR|不明確的失敗。|

## <a name="remarks"></a>備註
 原始檔控制批次用來跨多個專案或多個內容中執行相同的原始檔控制作業。 批次可用來在 批次作業期間消除多餘的對話方塊，從使用者體驗。 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)而`SccEndBatch`函式做為一組可用來表示的開頭和結尾的作業。 它們不能巢狀。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)