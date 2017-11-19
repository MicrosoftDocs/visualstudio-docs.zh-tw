---
title: "IDebugProcessEx2::Detach |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcessEx2::Detach
helpviewer_keywords: IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d810008391398741e644da7215de174918db604f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
這個方法會通知處理程序工作階段不會再偵錯程序。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Detach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Detach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pSession`  
 [in]可唯一識別要卸離此程序與工作階段值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 在傳遞介面`pSession`是被視為只有 cookie，值可唯一識別這原本偵錯工作階段管理員附加至這個處理序; 提供的介面上的方法都是的功能。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)