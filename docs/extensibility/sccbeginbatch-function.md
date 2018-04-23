---
title: SccBeginBatch 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5350484294d02356301839e38b97bea1d40ec27c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch 函式
此函式會啟動批次一連串的原始檔控制作業。 [SccEndBatch](../extensibility/sccendbatch-function.md)將被呼叫來結束批次。 這些批次可能不是巢狀。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>參數  
 無。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|批次的作業已成功開始。|  
|SCC_E_UNKNOWNERROR|不明確的失敗。|  
  
## <a name="remarks"></a>備註  
 原始檔控制批次用來跨多個專案或多個內容中執行相同的作業。 批次可以用於批次作業期間排除重複的每個專案對話方塊中，從 使用者經驗。 `SccBeginBatch`函式和[SccEndBatch](../extensibility/sccendbatch-function.md)做成對的函式用於表示開始和結束的作業。 它們不能巢狀。 `SccBeginBatch` 設定旗標，表示批次作業正在進行中。  
  
 批次作業時作用中，原始檔控制外掛程式應該向使用者最多顯示一個對話方塊中的任何問題，並將回應從該對話方塊中套用後續的所有作業。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)