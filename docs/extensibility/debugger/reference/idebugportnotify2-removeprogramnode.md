---
title: "IDebugPortNotify2::RemoveProgramNode |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortNotify2::RemoveProgramNode
helpviewer_keywords: IDebugPortNotify2::RemoveProgramNode
ms.assetid: 3668157b-66d2-416e-a359-fc04dcd18a48
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: efb3ca5e659782d50c7111d51cac970676dbaffd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportnotify2removeprogramnode"></a>IDebugPortNotify2::RemoveProgramNode
取消登錄從連接埠執行才能進行偵錯的程式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT RemoveProgramNode(   
   IDebugProgramNode2* pProgramNode  
);  
```  
  
```csharp  
int RemoveProgramNode(   
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pProgramNode`  
 [in][IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objecy 代表要移除註冊程式。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會移除已加入至呼叫程式節點[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)