---
title: GetValidCompatibleFramework 函式 |Microsoft 文件
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
ms.openlocfilehash: b28587b44dd98630538bc8d6d04c5bc6049e3ca9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="getvalidcompatibleframework-function"></a>GetValidCompatibleFramework 函式
  這個 API 支援 Office 基礎結構，並不適合直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*lpwszCompatibleFrameworksXML*|請勿使用。|  
|*pbstrValidFrameworkTag*|請勿使用。|  
  
## <a name="return-value"></a>傳回值  
 如果函式成功，它會傳回**S_OK**。 如果函式失敗，它會傳回錯誤碼。  
  
  