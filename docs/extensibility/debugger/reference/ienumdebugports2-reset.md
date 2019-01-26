---
title: IEnumDebugPorts2::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugPorts2::Reset
helpviewer_keywords:
- IEnumDebugPorts2::Reset
ms.assetid: 67da406c-eadb-421e-ae12-e26e9866f262
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5f2f7c852e3643c89522eb95b72ab573dd65808
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54980761"
---
# <a name="ienumdebugports2reset"></a>IEnumDebugPorts2::Reset
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
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 呼叫這個方法是，下一個呼叫之後[下一步](../../../extensibility/debugger/reference/ienumdebugports2-next.md)方法會傳回第一個元素的列舉型別。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)