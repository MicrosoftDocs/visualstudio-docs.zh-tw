---
title: "IDebugReference2::EnumChildren |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugReference2::EnumChildren
helpviewer_keywords: IDebugReference2::EnumChildren
ms.assetid: 35b3c2f3-69f4-4013-b555-f847221f62e8
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b5707920a9856b8a93611020ebbd23ae5f782300
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugreference2enumchildren"></a>IDebugReference2::EnumChildren
取得一份所選的子系的參考。 保留供未來使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumChildren (   
   DEBUGREF_INFO_FLAGS        dwFields,  
   DWORD                      dwRadix,  
   DBG_ATTRIB_FLAGS           dwAttribFilter,  
   LPCOLESTR                  pszNameFilter,  
   DWORD                      dwTimeout,  
   IEnumDebugReferenceInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumChildren (   
   enum_DEBUGREF_INFO_FLAGS     dwFields,  
   uint                         dwRadix,  
   enum_DBG_ATTRIB_FLAGS        dwAttribFilter,  
   string                       pszNameFilter,  
   uint                         dwTimeout,  
   out IEnumDebugReferenceInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwFields`  
 [in]從旗標的組合[DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)列舉，指定在列舉中的哪些欄位[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構會先填入。  
  
 `dwRadix`  
 [in]要用於格式化數字的任何資訊基數。  
  
 `dwAttribFilter`  
 [in]從旗標的組合[DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)用來做為篩選條件結合列舉`pszNameFilter`參數，以選取哪些結構的列舉。  
  
 `pszNameFilter`  
 [in]字串，指定的篩選，例如"MyX 」，用於搭配`dwAttribFilter`參數來選取要列舉的結構。  
  
 `dwTimeout`  
 [in]最大時間 （毫秒），從這個方法返回之前等候。 使用`INFINITE`無限期地等待。  
  
 `ppEnum`  
 [out]傳回[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)物件，其中包含要求的子屬性的清單。  
  
## <a name="return-value"></a>傳回值  
 一律傳回 `E_NOTIMPL`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)