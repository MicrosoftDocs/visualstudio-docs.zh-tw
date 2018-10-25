---
title: IDebugEvent2::GetAttributes |Microsoft Docs
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
ms.openlocfilehash: 515775a064d1e260d9eb028c6e1b6020b7d642cd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935298"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
取得這個偵錯事件的屬性。  
  
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
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面是通用於所有事件。 這個方法會描述類型的事件;比方說，是同步或非同步的事件，並就停止事件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)