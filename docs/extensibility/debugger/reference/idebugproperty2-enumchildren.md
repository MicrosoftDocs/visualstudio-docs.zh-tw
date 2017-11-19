---
title: "IDebugProperty2::EnumChildren |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::EnumChildren
helpviewer_keywords: IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 82f08fad921a2249e6a7943acec1fb9cb60e006b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
擷取屬性的子系清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumChildren (   
   DEBUGPROP_INFO_FLAGS      dwFields,  
   DWORD                     dwRadix,  
   REFGUID                   guidFilter,  
   DBG_ATTRIB_FLAGS          dwAttribFilter,  
   LPCOLESTR                 pszNameFilter,  
   DWORD                     dwTimeout,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumChildren (   
   enum_DEBUGPROP_INFO_FLAGS   dwFields,  
   uint                        dwRadix,  
   ref Guid                    guidFilter,  
   uint                        dwAttribFilter,  
   string                      pszNameFilter,  
   uint                        dwTimeout,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwFields`  
 [in]從旗標的組合[DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)列舉，指定在列舉中的哪些欄位[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構會先填入。  
  
 `dwRadix`  
 [in]指定要用於格式化數字的任何資訊的基數。  
  
 `guidFilter`  
 [in]篩選器搭配使用的 GUID`dwAttribFilter`和`pszNameFilter`參數，以選取哪些`DEBUG_PROPERTY_INFO`子系是要列舉。 例如，`guidFilterLocals`篩選器的本機變數。  
  
 `dwAttribFilter`  
 [in]從旗標的組合[DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)指定的物件，例如列舉類型的列舉型別`DBG_ATTRIB_METHOD`可能是這個屬性的子系的所有方法。 用於搭配`guidFilter`和`pszNameFilter`參數。  
  
 `pszNameFilter`  
 [in]搭配使用的篩選器名稱`guidFilter`和`dwAttribFilter`參數，以選取哪些`DEBUG_PROPERTY_INFO`子系是要列舉。 例如，此參數設定為"MyX 」 篩選條件具有名稱"MyX。 」 的所有子系  
  
 `dwTimeout`  
 [in]指定的時間上限，以毫秒為單位，從這個方法返回之前等候。 使用`INFINITE`無限期地等待。  
  
 `ppEnum`  
 [out]傳回[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)物件，其中包含子屬性的清單。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)