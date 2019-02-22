---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cbce46afaa6227f5d15720be8aebd4c60f5f236
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015494"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
這個方法可讓使用者附加至不安全的程序之前，顯示警告的連接埠提供者。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>傳回值  
 傳回的值如下所示：  
  
-   `S_OK`：附加至處理序是安全且沒有警告 對話方塊中會顯示。  
  
-   `S_FALSE`：附加可能有安全性問題，但有警告的對話方塊隨即顯示。  
  
-   `FAILURE`：附加至處理序就會失敗。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)