---
title: "IDebugPropertyCreateEvent2::GetDebugProperty |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPropertyCreateEvent2::GetDebugProperty
helpviewer_keywords: IDebugPropertyCreateEvent2::GetDebugProperty
ms.assetid: d7e43183-444c-4417-af19-82e28229f83a
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18657eb39de276b2da68699d642e35cf9112f99f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugpropertycreateevent2getdebugproperty"></a>IDebugPropertyCreateEvent2::GetDebugProperty
取得新的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDebugProperty (   
   IDebugProperty2** ppProperty  
);  
```  
  
```csharp  
int GetDebugProperty (   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppProperty`  
 [out]傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件，表示新屬性。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)