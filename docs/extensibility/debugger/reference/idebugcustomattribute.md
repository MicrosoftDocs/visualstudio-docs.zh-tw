---
title: "IDebugCustomAttribute |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomAttribute
helpviewer_keywords: IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 54bde0062fc6d79268a3c0d0a39989e493f4fb5c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
此介面代表自訂屬性，它可以提供名稱、 父節點和屬性的類別類型。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugCustomAttribute : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 符號提供者會實作這個介面以支援與符號相關聯的自訂屬性。 它通常是在自己的物件上實作。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[下一步](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)傳回此介面。 呼叫[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)方法會傳回[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugCustomAttribute`。  
  
|方法|說明|  
|------------|-----------------|  
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|取得要附加之目前屬性的欄位。|  
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|取得自訂屬性的類別類型。|  
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|取得自訂屬性的名稱。|  
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|取得 blob （位元組) 的屬性資訊。|  
  
## <a name="remarks"></a>備註  
 自訂屬性是 C#，提供特定類別或方法相關聯的自訂中繼資料結構。  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)