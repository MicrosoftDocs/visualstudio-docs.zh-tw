---
title: IDebugAddress |Microsoft Docs
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
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b620dfe22c16842b2bc887e669db45c86f6c4948
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49277026"
---
# <a name="idebugaddress"></a>IDebugAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個介面來表示項目的位址。 它會傳回符號處理常式。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugAddress : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 符號提供者會實作這個介面來代表物件的位址。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 在許多介面的許多方法會傳回此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|擷取[DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構描述的物件和其位置。|  
  
## <a name="remarks"></a>備註  
 符號提供者會傳回這個介面來代表物件和它的位置 （例如，函式、 方法或類別） 在特定範圍內。 會傳回此介面，並將其傳遞給各種方法的符號提供者和運算式評估工具。 一般來說，符號提供者是實體，必須將此介面的內容。  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)

