---
title: "IDebugStackFrame2::EnumProperties |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame2::EnumProperties
helpviewer_keywords: IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c2679317497568e9f844bcf9503fc0057ca6158c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
建立堆疊框架，例如本機變數與相關聯屬性的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumProperties (   
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,  
   UINT                      nRadix,  
   REFIID                    refiid,  
   DWORD                     dwTimeout,  
   ULONG*                    pcelt,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumProperties (   
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,  
   uint                        nRadix,  
   ref Guid                    refiid,  
   uint                        dwTimeout,  
   out uint                    pcelt,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwFieldSpec`  
 [in]從旗標的組合[DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)列舉，指定在列舉中的哪些欄位[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構會先填入。  
  
 `nRadix`  
 [in]要用於格式化數字的任何資訊基數。  
  
 `refiid`  
 [in]使用選取之篩選的 GUID [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構是要列舉，例如`guidFilterLocals`。  
  
 `dwTimeout`  
 [in]最大時間 （毫秒），從這個方法返回之前等候。 使用`INFINITE`無限期地等待。  
  
 `pcelt`  
 [out]傳回列舉的屬性數目。 這等同於呼叫[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)方法。  
  
 `ppEnum`  
 [out]傳回[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)物件，其中包含的所需的屬性清單。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會允許要透過單一呼叫中擷取所有選取的屬性，因為它的速度比循序呼叫[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)和[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)   
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)