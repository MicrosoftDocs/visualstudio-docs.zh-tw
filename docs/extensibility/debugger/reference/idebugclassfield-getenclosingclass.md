---
title: "IDebugClassField::GetEnclosingClass |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField::GetEnclosingClass
helpviewer_keywords: IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fbec5ac48280cf10bc89e73faca0779384bf3549
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
取得圍住儲存此類別的類別。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 [out]傳回[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件，表示封入類別。 如果沒有封入類別會傳回 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果此類別所表示[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件是巢狀的類別，然後在`ppClassField`參數傳回`IDebugClassField`物件，表示封入類別。 例如，指定此類別定義：  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 呼叫`GetEnclosingClass`方法`IDebugClassField`物件，代表`NestedClass`類別會傳回`IDebugClassField`代表類別物件`RootClass`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)