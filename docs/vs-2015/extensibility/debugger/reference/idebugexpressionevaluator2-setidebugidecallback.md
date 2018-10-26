---
title: IDebugExpressionEvaluator2::SetIDebugIDECallback |Microsoft Docs
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
- IDebugExpressionEvaluator2::SetIDebugIDECallback
- SetIDebugIDECallback
ms.assetid: f01c40ad-ef4b-477b-8304-602c6972bc88
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f1fc365b9fff1b611f6f13edbe5a56d3a94837b9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949496"
---
# <a name="idebugexpressionevaluator2setidebugidecallback"></a>IDebugExpressionEvaluator2::SetIDebugIDECallback
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

可讓要傳遞給運算式評估工具的回呼，在初始化期間的偵錯引擎。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT SetIDebugIDECallback (  
   IDebugIDECallback * pCallback  
);  
```  
  
```csharp  
int SetIDebugIDECallback (  
   IDebugIDECallback pCallback  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pCallback`  
 [in]回呼介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)

