---
title: IDebugIDECallback::DisplayMessage |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugIDECallback::DisplayMessage
ms.assetid: c19b48ee-b370-4fce-91fe-f82bf1e63179
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a0623daf4c5bb15db0235923d7563b1c13e9facb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugidecallbackdisplaymessage"></a>IDebugIDECallback::DisplayMessage
將指定的訊息字串傳送至偵錯工具的 [輸出] 視窗。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DisplayMessage (  
   LPCOLESTR szMessage  
);  
```  
  
```csharp  
int DisplayMessage (  
   string szMessage  
);  
```  
  
#### <a name="parameters"></a>參數  
 `szMessage`  
 [in]若要偵錯工具的 [輸出] 視窗中顯示的訊息字串。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)