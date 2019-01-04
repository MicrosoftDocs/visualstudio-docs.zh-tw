---
title: IDebugProcess2::CauseBreak |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::CauseBreak
helpviewer_keywords:
- IDebugProcess2::CauseBreak
ms.assetid: efda8865-2319-4d53-90bf-6d9d74cd5195
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7a52a360773443b1b179ad3cdec91f3924cedc9a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923016"
---
# <a name="idebugprocess2causebreak"></a>IDebugProcess2::CauseBreak
下一步 也就是程式執行的程式碼，在此程序中的要求會中止，並傳送[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)事件物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CauseBreak(   
   void  
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)