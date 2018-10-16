---
title: IDebugSettingsCallback2::GetEEMetricDword |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricDword
ms.assetid: c5f8f417-0ef0-4fd0-a779-b0a8ead4effe
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 422daf0ce6b4a417f0a60f79c9aef2f408096f11
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49216602"
---
# <a name="idebugsettingscallback2geteemetricdword"></a>IDebugSettingsCallback2::GetEEMetricDword
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

擷取對應至的運算式評估工具的指定計量的值。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetEEMetricDword(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   DWORD*  pdwValue  
);  
```  
  
```csharp  
private int GetEEMetricDword(  
   ref Guid guidLang,  
   ref Guid guidVendor,  
   string   pszMetric,  
   out uint pdwValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `guidLang`  
 [in]程式設計語言的唯一識別碼。  
  
 `guidVendor`  
 [in]供應商的唯一識別碼。  
  
 `pszMetric`  
 [in]計量名稱。  
  
 `pdwValue`  
 [out]傳回度量的字串對應的值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)

