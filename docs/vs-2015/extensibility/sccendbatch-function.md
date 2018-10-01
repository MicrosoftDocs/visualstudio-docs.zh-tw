---
title: SccEndBatch 函式 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 075e661976062d2de985fa52110ea87840c2ab21
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487019"
---
# <a name="sccendbatch-function"></a>SccEndBatch 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[SccEndBatch 函式](https://docs.microsoft.com/visualstudio/extensibility/sccendbatch-function)。  
  
此函式結束時，原始檔控制作業的批次。 這些批次可能不是巢狀。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
SCCRTN SccEndBatch(void);  
```  
  
#### <a name="parameters"></a>參數  
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
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)

