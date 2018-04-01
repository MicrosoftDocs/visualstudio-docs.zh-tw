---
title: IDebugClassField::DoesInterfaceExist |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8d0e4535417f80198f06cb6b4255fea209b701e8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
決定特定的介面定義在類別中。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DoesInterfaceExist(   
   LPCOLESTR pszInterfaceName  
);  
```  
  
```csharp  
int DoesInterfaceExist(  
   [In] string pszInterfaceName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszInterfaceName`  
 [in]字串，包含要尋找的介面名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回 S_OK 時，會傳回 S_FALSE 如果介面不存在。反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法實際上取得所有介面的列舉型別，並搜尋相符的介面清單。  
  
## <a name="see-also"></a>請參閱  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)