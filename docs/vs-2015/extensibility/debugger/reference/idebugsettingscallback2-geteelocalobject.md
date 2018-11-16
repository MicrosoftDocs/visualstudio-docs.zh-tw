---
title: IDebugSettingsCallback2::GetEELocalObject |Microsoft Docs
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
- IDebugSettingsCallback2::GetEELocalObject
ms.assetid: e69a3469-a049-420c-b918-c48a1e7b9baf
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 14ee687700aadb4eff0ab4fa160cf8ac339de54b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769858"
---
# <a name="idebugsettingscallback2geteelocalobject"></a>IDebugSettingsCallback2::GetEELocalObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

擷取給定的計量名稱的運算式的評估工具本機物件。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetEELocalObject(  
   REFGUID     guidLang,  
   REFGUID     guidVendor,  
   LPCWSTR     pszMetric,  
   IUnknown ** ppUnk  
);  
```  
  
```csharp  
private int GetEELocalObject(  
   ref Guid          guidLang,  
   ref Guid          guidVendor,  
   string            pszMetric,  
   out System.Object ppUnk  
);  
```  
  
#### <a name="parameters"></a>參數  
 `guidLang`  
 [in]程式設計語言的唯一識別碼。  
  
 `guidVendor`  
 [in]供應商的唯一識別碼。  
  
 `pszMetric`  
 [in]計量名稱。  
  
 `ppUnk`  
 [out]傳回的運算式評估工具的本機物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)

