---
title: IDebugObject2：： GetBackingFieldForProperty |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5eadbed61638ff1442c4ed7033426e245abf930a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62536382"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得欄位或變數 (是否有任何可支援此物件所表示之屬性的) 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppObject`  
 擴展描述支援欄位的 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) 物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)物件代表 managed 程式碼類別屬性，也就是具有 get 和/或 set 存取子的方法。 這類屬性通常需要變數以包含屬性所操作的值。 此變數稱為支援欄位。 如果物件沒有支援欄位，則請務必傳回 null 值：某些呼叫端可能不會注意傳回值，而是會查看是否已在中傳回 null 值 `ppObject` 。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
