---
title: GetValidCompatibleFramework 函式
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b93e0de5f1d8c1d4e93189e7bfee36d44db19319
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648874"
---
# <a name="getvalidcompatibleframework-function"></a>GetValidCompatibleFramework 函式
  此 API 支援 Office 基礎結構，但不適合直接從您的程式碼使用。  

## <a name="syntax"></a>語法  

```csharp 
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  

### <a name="parameters"></a>參數  

|參數|描述|  
|---------------|-----------------|  
|*lpwszCompatibleFrameworksXML*|請勿使用。|  
|*pbstrValidFrameworkTag*|請勿使用。|  

## <a name="return-value"></a>傳回值  
 如果此函數就會成功，它會傳回**S_OK**。 如果函式失敗，它會傳回錯誤碼。  

