---
title: IDebugProcess2::Detach |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fce67b16d8de1e70e308fd107af3c26012e752c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
會從這個處理序偵錯工具中斷連結卸離所有處理序中的程式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Detach(   
   void   
);  
```  
  
```csharp  
int Detach();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 所有程式和處理程序繼續執行，但不會再偵錯工作階段的一部分。 在卸離後作業已完成，沒有其他偵錯此處理程序 （以及它的程式） 的事件將會傳送。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)