---
title: SccBeginBatch Function | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: f4b6b0f30b639ff660534511563b78aa1dc14f8e
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="sccbeginbatch-function"></a>SccBeginBatch Function
This function starts a batch sequence of source control operations. The [SccEndBatch](../extensibility/sccendbatch-function.md) will be called to end the batch. These batches may not be nested.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>Parameters  
 None.  
  
## <a name="return-value"></a>Return Value  
 The source control plug-in implementation of this function is expected to return one of the following values:  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Batch of operations successfully began.|  
|SCC_E_UNKNOWNERROR|Nonspecific failure.|  
  
## <a name="remarks"></a>Remarks  
 Source control batches are used to execute the same operations across multiple projects or multiple contexts. Batches can be used to eliminate redundant per-project dialog boxes from the user experience during a batched operation. The `SccBeginBatch` function and the [SccEndBatch](../extensibility/sccendbatch-function.md) are used as a function pair to indicate the beginning and end of an operation. They cannot be nested. `SccBeginBatch` sets a flag indicating that a batch operation is in progress.  
  
 While a batch operation is in effect, the source control plug-in should present at most one dialog box for any question to the user and apply the response from that dialog box on all subsequent operations.  
  
## <a name="see-also"></a>See Also  
 [Source Control Plug-in API Functions](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)
