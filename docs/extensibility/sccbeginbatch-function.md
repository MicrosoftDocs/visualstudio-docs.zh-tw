---
title: SccBeginBatch 功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c7982d8c8c0d71f8c79e9b808be5453d384882d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701190"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch 功能
此函數啟動源控制操作的批處理序列。 將調用[SccEndBatch](../extensibility/sccendbatch-function.md)以結束批處理。 這些批次可能無法嵌套。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>參數
 無。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|批量操作已成功啟動。|
|SCC_E_UNKNOWNERROR|非特異性故障。|

## <a name="remarks"></a>備註
 原始程式碼管理批次處理用於跨多個專案或多個上下文執行相同的操作。 批次處理可用於在批次處理操作期間從使用者體驗中消除每個專案的冗餘對話框。 函數`SccBeginBatch`和[SccEndBatch](../extensibility/sccendbatch-function.md)用作函數對,以指示操作的開始和結束。 它們不能嵌套。 `SccBeginBatch`設置指示批處理操作正在進行的標誌。

 當批處理操作生效時,原始程式碼管理外掛程式應最多向使用者顯示一個對話框,用於任何問題,並將該對話框的回應應用於所有後續操作。

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 功能](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
