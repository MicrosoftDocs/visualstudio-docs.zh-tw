---
title: IDebugSettingsCallback2::GetMetricDword |Microsoft Docs
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
- IDebugSettingsCallback2::GetMetricDword
ms.assetid: 831a5a1a-c4af-4520-9fdf-3a731aeff85c
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8186d1330731a6292def22c94c0f0e3bb0c19ed
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895609"
---
# <a name="idebugsettingscallback2getmetricdword"></a>IDebugSettingsCallback2::GetMetricDword
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

擷取值，指定其名稱的度量資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetMetricDword(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD*  pdwValue  
);  
```  
  
```csharp  
private int GetMetricDword(  
   string   pszType,  
   ref Guid guidSection,  
   string   pszMetric,  
   out uint pdwValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszType`  
 [in]度量的類型。  
  
 `guidSection`  
 [in]區段的唯一識別碼。  
  
 `pszMetric`  
 [in]計量名稱。  
  
 `pdwValue`  
 [out]傳回的度量值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)

