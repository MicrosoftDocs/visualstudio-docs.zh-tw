---
title: "IDebugPortEx2::CanTerminateProcess |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortEx2::CanTerminateProcess
helpviewer_keywords: IDebugPortEx2::CanTerminateProcess
ms.assetid: 111f65d8-5a1a-42b3-9de3-dd9bb03a33fd
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1b256be2c354f680fe4ce4d898a3d60107956d80
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportex2canterminateprocess"></a>IDebugPortEx2::CanTerminateProcess
決定是否可以終止處理程序。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CanTerminateProcess(   
   IDebugProcess2* pPortProcess  
);  
```  
  
```csharp  
HRESULT CanTerminateProcess(   
   IDebugProcess2 pPortProcess  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pPortProcess`  
 [in][IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)物件，表示終止程序。  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`可以終止處理程序; 否則傳回`S_FALSE`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)