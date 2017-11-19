---
title: "IDebugClassField |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField
helpviewer_keywords: IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c9c827c8c72ddf323848e9744edbdcda9a51b2f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugclassfield"></a>IDebugClassField
此介面為型別表示的類別。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugClassField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 符號提供者會實作此介面實作在相同物件上[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面。 這個介面是代表類別類型的特製化。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 介面的數目有方法可傳回此介面包括[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)， [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)，和[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)。 此外，您可以使用[QueryInterface](/cpp/atl/queryinterface)獲得從這個介面[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)方法傳回的旗標`FIELD_TYPE_CLASS`。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了上[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)和[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面，這個介面會實作下列：  
  
|方法|說明|  
|------------|-----------------|  
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|建立這個類別的基底類別的列舉值。|  
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|決定特定的介面定義在類別中。|  
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|建立這個類別的巢狀類別的列舉值。|  
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|取得圍住儲存此類別的類別。|  
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|建立這個類別所實作之介面的列舉值。|  
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|建立這個類別的建構函式的列舉值。|  
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|取得預設索引子名稱。|  
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|建立這個類別的巢狀的列舉值的列舉值。|  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)