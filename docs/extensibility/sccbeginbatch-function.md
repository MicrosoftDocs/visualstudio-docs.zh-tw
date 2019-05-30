---
title: SccBeginBatch 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6bb145358184117046e14b7b598ce6d4bb4586b0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333890"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch 函式
此函式會啟動批次一連串的原始檔控制作業。 [SccEndBatch](../extensibility/sccendbatch-function.md)將被呼叫來結束批次。 這些批次可能不是巢狀。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>參數
 無。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：

|值|描述|
|-----------|-----------------|
|SCC_OK|批次的作業已成功開始。|
|SCC_E_UNKNOWNERROR|不明確的失敗。|

## <a name="remarks"></a>備註
 原始檔控制批次用來跨多個專案或多個內容中執行相同的作業。 批次可用來在 批次作業期間消除多餘的每個專案對話方塊，從使用者體驗。 `SccBeginBatch`函式與[SccEndBatch](../extensibility/sccendbatch-function.md)函式組的形式來表示的開頭和結尾的作業。 它們不能巢狀。 `SccBeginBatch` 設定旗標，表示批次作業正在進行中。

 批次作業生效時，原始檔控制外掛程式應該向使用者顯示最多一的對話方塊中，針對任何問題，並從該對話方塊回應套用於所有後續的作業。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)