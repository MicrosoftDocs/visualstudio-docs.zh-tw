---
title: IDebugArrayField |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ef60550dcea362fd196ba2740d7347981a6d01bb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745639"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面描述陣列符號或類型。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugArrayField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 符號提供者所實作的相同物件上實作這個介面[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面。 這個介面是特製化，表示陣列物件。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 使用[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)若要取得從這個介面[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)傳回的旗標`FIELD_TYPE_ARRAY`。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 上的方法除了[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)並[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面，這個介面會實作下列：  
  
|方法|描述|  
|------------|-----------------|  
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|取得陣列中的項目數。|  
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|取得項目的型別陣列中。|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|取得陣列的陣序規範。|  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

