---
title: SccBeginBatch 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e79a1203d97bfbf105a69b97516bda307825bd99
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952131"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch 函式
此函式會啟動原始檔控制作業的批次序列。 將呼叫 [SccEndBatch](../extensibility/sccendbatch-function.md) 以結束批次。 這些批次可能不會被嵌套。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>參數
 無。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|作業批次已成功開始。|
|SCC_E_UNKNOWNERROR|模糊失敗。|

## <a name="remarks"></a>備註
 原始檔控制批次是用來跨多個專案或多個內容執行相同的作業。 批次可在批次作業期間，用來從使用者體驗中消除重複的每個專案對話方塊。 `SccBeginBatch`函數和[SccEndBatch](../extensibility/sccendbatch-function.md)會用來做為函陣列，以指出作業的開頭和結尾。 它們無法進行嵌套。 `SccBeginBatch` 設定旗標，表示批次作業正在進行中。

 當批次作業有效時，原始檔控制外掛程式最多應該會針對使用者的任何問題顯示最多一個對話方塊，並在所有後續作業上套用該對話方塊的回應。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
