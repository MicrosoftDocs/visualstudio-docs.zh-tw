---
title: IDebugProcess2::CanDetach |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess2::CanDetach
helpviewer_keywords:
- IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1c160fb10ce4ebdd8d483da5f1ccbd7efaa6d685
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess2candetach"></a>IDebugProcess2::CanDetach
決定是否工作階段的偵錯管理員 (SDM) 可以卸離程序。  
  
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
 如果成功，傳回`S_OK.`傳回`S_FALSE`如果偵錯工具無法從處理序中斷連結。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)