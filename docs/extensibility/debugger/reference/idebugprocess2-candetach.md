---
title: IDebugProcess2::CanDetach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::CanDetach
helpviewer_keywords:
- IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f092fc0ec8467a6b78addff50b3d8d8f37ee29d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53962911"
---
# <a name="idebugprocess2candetach"></a>IDebugProcess2::CanDetach
判斷工作階段的偵錯管理員 (SDM) 可以中斷連結程序。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CanDetach(  
   void  
);  
```  
  
```csharp  
int CanDetach();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK.`傳回`S_FALSE`如果偵錯工具無法從處理序中斷連結。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)