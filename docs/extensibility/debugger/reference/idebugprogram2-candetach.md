---
title: IDebugProgram2::CanDetach |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 08387df82b20ef38380fe6302a5ca1f5d0bcbc9c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
決定偵錯引擎 (DE) 可以中斷程式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CanDetach(  
   void  
);  
```  
  
```csharp  
int CanDetach();  
```  
  
## <a name="return-value"></a>傳回值  
 如果卸離，傳回`S_OK`; 否則傳回錯誤碼。 傳回`S_FALSE`如果 DE 無法中斷連結的程式。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)