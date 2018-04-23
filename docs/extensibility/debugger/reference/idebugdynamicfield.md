---
title: IDebugDynamicField |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 378107570f50369ae46c609b0fe2e5099d5adab6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
此介面代表變數的類型。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugDynamicField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 符號提供者會實作這個介面，可以在執行階段決定的任何類型的基底類別。 這是 managed 程式碼。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 此介面代表可從中衍生更具特製化的介面的基底類別。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 這個介面並不提供任何方法以外繼承自`IDebugField`。  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)