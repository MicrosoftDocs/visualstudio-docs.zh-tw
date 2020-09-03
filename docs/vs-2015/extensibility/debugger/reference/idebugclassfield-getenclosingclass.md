---
title: IDebugClassField：： GetEnclosingClass |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 896d3ecd5202bf85e6b9e86af31796c662a6eef1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191003"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得括住這個類別的類別。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```csharp  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppClassField`  
 擴展傳回代表封閉類別的 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 物件。 如果沒有封入類別，則會傳回 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果這個 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 物件所代表的類別是嵌套類別，則參數會傳回 `ppClassField` 代表封入 `IDebugClassField` 類別的物件。 例如，假設有這個類別定義：  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 `GetEnclosingClass`在代表類別的物件上呼叫方法，會傳回 `IDebugClassField` `NestedClass` `IDebugClassField` 代表類別的物件 `RootClass` 。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
