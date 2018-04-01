---
title: IDebugBinder::Bind |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 83b1697d2f10cc656e4c7daa2599f7754cef9466
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
這個方法會取得的記憶體內容或包含符號的目前值的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Bind(   
   IDebugObject*  pContainer,  
   IDebugField*   pField,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Bind(  
   IDebugObject     pContainer,  
   IDebugField      pField,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pContainer`  
 [in][IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ，其中包含所參考的子系`pField`。  
  
 `pField`  
 [in][IDebugField](../../../extensibility/debugger/reference/idebugfield.md)表示符號。  
  
 `ppObject`  
 [out]傳回`IDebugObject`表示符號的執行個體。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)