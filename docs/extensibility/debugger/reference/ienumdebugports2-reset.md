---
title: IEnumDebugPorts2::Reset |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugPorts2::Reset
helpviewer_keywords:
- IEnumDebugPorts2::Reset
ms.assetid: 67da406c-eadb-421e-ae12-e26e9866f262
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ead521af376388c73aae045d3586a70f55cc8418
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
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
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 呼叫這個方法是下, 一次呼叫之後[下一步](../../../extensibility/debugger/reference/ienumdebugports2-next.md)方法會傳回第一個元素的列舉型別。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)