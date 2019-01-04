---
title: GetValidCompatibleFramework 函式
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 30a116993535e3b99b4e91edf07752c00a020859
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835483"
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
