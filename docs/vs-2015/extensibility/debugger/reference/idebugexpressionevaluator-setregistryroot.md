---
title: IDebugExpressionEvaluator::SetRegistryRoot | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot
helpviewer_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot method
ms.assetid: 790886d8-1975-4d3c-9a75-cd86c1faf4ca
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3e01c340b571854011966e9feeef116fab0b7d41
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945965"
---
# <a name="idebugexpressionevaluatorsetregistryroot"></a>IDebugExpressionEvaluator::SetRegistryRoot
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個方法設定的登錄根目錄。 用於並排顯示偵錯。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT SetRegistryRoot (   
   LPCOLESTR ustrRegistryRoot  
);  
```  
  
```csharp  
int SetRegistryRoot(  
   string ustrRegistryRoot  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ustrRegistryRoot`  
 [in]新的登錄根目錄。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 運算式評估工具會先具現化，並點時，通常設定指定的登錄根登錄機碼的 Visual Studio 特定版本 (hkey_local_machine\software\microsoft\visualstudio \\\*X.Y*，其中 *X.Y* 是版本號碼)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
