---
title: "IDebugPortNotify2::AddProgramNode |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortNotify2::AddProgramNode
helpviewer_keywords: IDebugPortNotify2::AddProgramNode
ms.assetid: 34c0e949-1eb9-4108-9cb8-a3eb87fcf190
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: edaa591e79f48c86188510be90ebefc0690adad5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportnotify2addprogramnode"></a>IDebugPortNotify2::AddProgramNode
註冊可偵錯的程式與連接埠執行。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT AddProgramNode(   
   IDebugProgramNode2* pProgramNode  
);  
```  
  
```csharp  
int AddProgramNode(   
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pProgramNode`  
 [in][IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件，表示要登錄的程式。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 程式節點可以取消註冊該連接埠從藉由呼叫[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)