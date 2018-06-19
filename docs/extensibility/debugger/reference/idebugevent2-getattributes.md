---
title: IDebugEvent2::GetAttributes |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d6305d7000456eb81cf01c9e85e6c2a421ed800
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121813"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
這個偵錯事件中取得的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetAttribute(   
   DWORD* pdwAttrib  
);  
```  
  
```csharp  
int GetAttribute(   
   out uint pdwAttrib  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwAttrib`  
 [out]從旗標的組合[EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)列舉型別。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面是通用於所有事件。 這個方法會描述類型的事件。比方說，是同步或非同步的事件，且它停止事件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)