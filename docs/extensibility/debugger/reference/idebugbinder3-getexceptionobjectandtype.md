---
title: "IDebugBinder3::GetExceptionObjectAndType |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords: IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b698295f3bfff9fb2c16e286b85bf5268bf6e852
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
如果有的話，這個方法會擷取與物件相關聯的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```csharp  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppException`  
 [out]傳回表示例外狀況的物件。  
  
 `ppField`  
 [out]傳回物件，表示可能造成的例外狀況 （這可能是 null 值） 的特定欄位。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
> [!NOTE]
>  若要確認是否有例外狀況，請檢查所傳回的值`ppException`： 如果它是 null 值，則任何例外狀況不是此物件相關聯。  
  
## <a name="see-also"></a>請參閱  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)