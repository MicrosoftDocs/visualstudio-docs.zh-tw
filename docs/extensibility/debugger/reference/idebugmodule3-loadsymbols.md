---
title: "IDebugModule3::LoadSymbols |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule3::LoadSymbols
helpviewer_keywords: IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 88789800e0e93f07b953417214bde8852def32f1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
載入目前模組的符號。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT LoadSymbols(  
   void  
);  
```  
  
```csharp  
int LoadSymbols();  
```  
  
## <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回`S_OK`。 如果失敗，它會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會將目前的搜尋路徑中載入符號 (這可以藉由呼叫更改[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)方法)。  
  
 這個方法是透過慣用[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)