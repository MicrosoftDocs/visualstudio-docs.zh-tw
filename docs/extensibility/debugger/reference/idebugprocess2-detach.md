---
title: "IDebugProcess2::Detach |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::Detach
helpviewer_keywords: IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 37e642c8aa8709de28ea70d1a9d303877df25267
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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