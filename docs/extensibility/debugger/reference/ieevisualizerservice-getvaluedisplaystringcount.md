---
title: IEEVisualizerService::GetValueDisplayStringCount | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: bde584e57e285886ae6d80ebe5afb699ceee70a3
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Retrieves the number of value strings to display for the specified property or field.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetValueDisplayStringCount (  
   DWORD         displayKind,   
   IDebugField * propertyOrField,   
   ULONG *       pcelt  
);  
```  
  
```cs  
int GetValueDisplayStringCount (  
   uint        displayKind,   
   IDebugField propertyOrField,   
   out ulong   pcelt  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `displayKind`  
 [in] Value from the [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) enumeration.  
  
 `propertyOrField`  
 [in] An [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface that represents a property or field.  
  
 `pcelt`  
 [out] Returns the number of value strings to display.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="see-also"></a>See Also  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
