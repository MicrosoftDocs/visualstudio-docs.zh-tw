---
title: "IDebugEngine3::LoadSymbols |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine3::LoadSymbols
helpviewer_keywords: IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ad486256b194ae0f03ed3fe41c23a71f2f9159c8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
此偵錯引擎進行偵錯的所有模組 （視） 載入符號。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT LoadSymbols();  
```  
  
```csharp  
int LoadSymbols();  
```  
  
#### <a name="parameters"></a>參數  
 無。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這會載入這個偵錯引擎所參考的所有模組的偵錯符號。 它們不已經載入時，才會載入的符號。 符號會搜尋呼叫所設定的路徑上[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)