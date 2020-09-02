---
title: IDebugProperty2：： SetValueAsString |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d50057570b5b067447321f975d4d33da8aa3de43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193435"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

從指定的字串設定屬性的值。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   UINT      nRadix,  
   DWORD     dwTimeout  
);  
```  
  
```csharp  
int SetValueAsString (   
   string pszValue,  
   uint   nRadix,  
   uint   dwTimeout  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszValue`  
 在字串，包含要設定的值。  
  
 `nRadix`  
 在用來解讀任何數值資訊的基數。 這可以是0，以嘗試自動判斷基數。  
  
 `dwTimeout`  
 在指定從這個方法傳回之前等候的最長時間（以毫秒為單位）。 使用 `INFINITE` 可無限期等候。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼。 下表顯示其他可能的值。  
  
|值|描述|  
|-----------|-----------------|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|無法將字串轉換成屬性值，或無法設定屬性值。|  
|`E_SETVALUE_VALUE_IS_READONLY`|此為唯讀屬性。|  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
