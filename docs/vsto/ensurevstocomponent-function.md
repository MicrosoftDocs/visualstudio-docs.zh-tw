---
title: "EnsureVSTOComponent 函式 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: e101fcd5-37a2-4b8c-b9ac-a84624298736
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 98dfa5c201889354f880b2076af4f949407a9b0a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ensurevstocomponent-function"></a>EnsureVSTOComponent 函式
  這個 API 支援 Office 基礎結構，並不適合直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnsureVSTOComponent(  
    IVSTProject *pProject  
);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|*pProject*|請勿使用。|  
  
## <a name="return-value"></a>傳回值  
 如果函式成功，它會傳回**S_OK**。 如果函式失敗，它會傳回錯誤碼。  
  
  