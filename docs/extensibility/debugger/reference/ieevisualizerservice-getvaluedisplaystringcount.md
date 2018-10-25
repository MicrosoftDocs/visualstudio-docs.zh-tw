---
title: IEEVisualizerService::GetValueDisplayStringCount |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5ef642e48ee4389e48c1141c18a70f9ad5d0b793
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949665"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
擷取值的字串，以顯示指定的屬性或欄位的數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetValueDisplayStringCount (  
   DWORD         displayKind,   
   IDebugField * propertyOrField,   
   ULONG *       pcelt  
);  
```  
  
```csharp  
int GetValueDisplayStringCount (  
   uint        displayKind,   
   IDebugField propertyOrField,   
   out ulong   pcelt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `displayKind`  
 [in]值從[DisplayKind](../../../extensibility/debugger/reference/displaykind.md)列舉型別。  
  
 `propertyOrField`  
 [in][IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面，表示屬性或欄位。  
  
 `pcelt`  
 [out]傳回值要顯示的字串數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)