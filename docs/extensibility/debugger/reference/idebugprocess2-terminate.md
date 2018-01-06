---
title: "IDebugProcess2::Terminate |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::Terminate
helpviewer_keywords: IDebugProcess2::Terminate
ms.assetid: 5e6bf373-0fe9-4321-b04a-473a65f664d9
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5c3bed9f3df7266a12d8cd8c39f16955fa647c04
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess2terminate"></a>IDebugProcess2::Terminate
終止處理序。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 當終止處理程序時，會終止該處理序內的所有程式。沒有任何可以執行任何更多的程式碼。  
  
## <a name="see-also"></a>請參閱  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)