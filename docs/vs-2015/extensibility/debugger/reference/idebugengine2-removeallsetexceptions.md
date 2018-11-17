---
title: IDebugEngine2::RemoveAllSetExceptions |Microsoft Docs
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
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2fbffeb2ec329436e0913feba83464aa928c0bb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740112"
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

移除 IDE 已設定特定的執行階段架構或語言的例外狀況的清單。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT RemoveAllSetExceptions(   
   REFGUID guidType  
);  
```  
  
```csharp  
int RemoveAllSetExceptions(   
   ref Guid guidType  
);  
```  
  
#### <a name="parameters"></a>參數  
 `guidType`  
 [in]語言 GUID 或執行階段架構特有的偵錯引擎的 GUID。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 移除這個方法的例外狀況由先前呼叫設定[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)方法。  
  
 若要移除特定的例外狀況，請呼叫[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)

