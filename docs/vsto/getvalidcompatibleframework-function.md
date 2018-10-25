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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8cc16544df224e09724cae8a1f09f72039cb61e5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894491"
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

