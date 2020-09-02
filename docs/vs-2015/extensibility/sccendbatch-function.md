---
title: SccEndBatch 函式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 986056b1f5202c2fb94d27a8792ed3b0fe308944
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200139"
---
# <a name="sccendbatch-function"></a>SccEndBatch 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此函式會結束原始檔控制作業的批次。 這些批次可能不會被嵌套。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
SCCRTN SccEndBatch(void);  
```  
  
#### <a name="parameters"></a>參數  
 無。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|作業批次已成功結束。|  
|SCC_E_UNKNOWNERROR|模糊失敗。|  
  
## <a name="remarks"></a>備註  
 原始檔控制批次是用來跨多個專案或多個內容執行相同的原始檔控制作業。 批次可在批次作業期間，用來消除使用者體驗中的多餘對話方塊。 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)和 `SccEndBatch` 函數是用來做為配對，以指出作業的開頭和結尾。 它們無法進行嵌套。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
