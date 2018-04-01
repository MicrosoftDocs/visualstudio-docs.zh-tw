---
title: IEnumDebugBoundBreakpoints2::Reset |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugBoundBreakpoints2::Reset
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2::Reset
ms.assetid: 0f0522a5-6a97-4c4e-859b-cc4476e6c527
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7348cc4b6589cea7744162ab7870be6ddb2e3ade
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugboundbreakpoints2reset"></a>IEnumDebugBoundBreakpoints2::Reset
將列舉重設第一個項目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 呼叫這個方法是下, 一次呼叫之後[下一步](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)方法會傳回第一個元素的列舉型別。  
  
## <a name="see-also"></a>請參閱  
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)