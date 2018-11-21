---
title: IEEVisualizerService::GetValueDisplayStringCount |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 412a2585a35c7503f99207050d07d3b27d434e99
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764065"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

擷取值的字串，以顯示指定的屬性或欄位的數目。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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

