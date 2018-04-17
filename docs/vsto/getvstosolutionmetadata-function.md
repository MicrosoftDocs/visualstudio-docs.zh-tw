---
title: GetVstoSolutionMetadata 函式 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6c024d97d13c2794dd4fdaee6cfcd53d24c2e668
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="getvstosolutionmetadata-function"></a>GetVstoSolutionMetadata 函式
  這個 API 支援 Office 基礎結構，並不適合直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT WINAPI GetVstoSolutionMetadata(  
    LPCWSTR lpwszSolutionMetadataKey,  
    ISolutionMetadata** ppSolutionInfo  
);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*lpwszSolutionMetadataKey*|請勿使用。|  
|*ppSolutionInfo*|請勿使用。|  
  
## <a name="return-value"></a>傳回值  
 如果函式成功，它會傳回**S_OK**。 如果函式失敗，它會傳回錯誤碼。  
  
  