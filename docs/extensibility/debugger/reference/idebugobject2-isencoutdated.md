---
title: IDebugObject2::IsEncOutdated |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ab51e2dbc75de33bcafe28295b5e47e4b4358538
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
這個方法會判斷是否已過期或父容器的此物件的編輯後繼續狀態。 自訂運算式評估工具不會實作這個方法，一律會傳回`E_NOTIMPL`。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```csharp  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pfEncOutdated`  
 [out]非零 (`TRUE`) 如果編輯後繼續狀態為過期，零 (`FALSE`) 如果不是。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
> [!NOTE]
>  自訂運算式評估工具應該會一律傳回`E_NOTIMPL`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)