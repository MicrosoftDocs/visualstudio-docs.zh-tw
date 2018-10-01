---
title: IEnumDebugPropertyInfo2::Next |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugPropertyInfo2::Next
helpviewer_keywords:
- IEnumDebugPropertyInfo2::Next
ms.assetid: 4eb8c7c3-aadf-4187-abee-c0620308a3eb
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 21236d353daccffef93c0266b466e409414d2a6b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497968"
---
# <a name="ienumdebugpropertyinfo2next"></a>IEnumDebugPropertyInfo2::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IEnumDebugPropertyInfo2::Next](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugpropertyinfo2-next)。  
  
從列舉中傳回下的一個項目集。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Next(  
   ULONG                 celt,  
   DEBUG_PROPERTY_INFO** rgelt,  
   ULONG*                pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint                  celt,  
   DEBUG_PROPERTY_INFO[] rgelt,  
   ref uint              pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in]若要擷取的元素數目。 也會指定的大小上限`rgelt`陣列。  
  
 `rgelt`  
 [in、 out]陣列[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)来填入的項目。  
  
 `pceltFetched`  
 [out]傳回的項目數中實際傳回`rgelt`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`。 傳回`S_FALSE`更少的項目要求的數目可能會傳回; 否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)

