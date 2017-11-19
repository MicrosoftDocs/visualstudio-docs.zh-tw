---
title: "IEnumDebugPropertyInfo2::Next |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugPropertyInfo2::Next
helpviewer_keywords: IEnumDebugPropertyInfo2::Next
ms.assetid: 4eb8c7c3-aadf-4187-abee-c0620308a3eb
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f21240a63caa9fcb00b59a6937479910dfa99435
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugpropertyinfo2next"></a>IEnumDebugPropertyInfo2::Next
列舉中傳回下一個項目的集合。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 [in]若要擷取的項目數目。 也會指定的大小上限`rgelt`陣列。  
  
 `rgelt`  
 [in、 out]陣列[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)要填入的項目。  
  
 `pceltFetched`  
 [out]傳回的項目數中實際傳回`rgelt`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`。 傳回`S_FALSE`如果無法傳回要求的元素數目少於; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)