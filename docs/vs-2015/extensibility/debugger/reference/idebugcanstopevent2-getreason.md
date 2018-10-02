---
title: IDebugCanStopEvent2::GetReason |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fcc130a2b6dc1874c1ac536ae2e7d13aa3db4952
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491588"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugCanStopEvent2::GetReason](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcanstopevent2-getreason)。  
  
取得偵錯引擎 (DE) 為何想要停止的原因。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```csharp  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcr`  
 [out]傳回值，以從[CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)列舉，描述這個事件的原因。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法通常會呼叫之前[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)方法，讓呼叫者可以判斷是否要傳遞非零 (`TRUE`) 來`IDebugCanStopEvent2::CanStop`方法。  
  
 正在停止的原因可以是`CANSTOP_ENTRYPOINT`，這表示裝置已達到進入點，或`CANSTOP_STEPIN`，這表示 DE 已逐步執行函式。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)

