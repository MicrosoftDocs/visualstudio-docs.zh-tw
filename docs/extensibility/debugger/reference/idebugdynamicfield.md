---
title: "IDebugDynamicField |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDynamicField
helpviewer_keywords: IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5bb632d2ca51090f88b33ea6a8365fa9ac13ba9f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)