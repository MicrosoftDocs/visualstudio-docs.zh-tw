---
title: IDebugEngine3::LoadSymbols |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
caps.latest.revision: 7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 97509031e123babf5febfd51ebff3047e5d21ccf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>請參閱  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)