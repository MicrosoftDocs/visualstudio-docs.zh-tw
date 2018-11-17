---
title: IDebugProcessSecurity::QueryCanSafelyAttach |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 357ab447d0f16c3bbbfb656d042c0095df01bc83
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784438"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個方法可讓使用者附加至不安全的程序之前，顯示警告的連接埠提供者。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>傳回值  
 傳回的值如下所示：  
  
-   `S_OK`： 附加至處理序是安全且沒有警告 對話方塊中會顯示。  
  
-   `S_FALSE`： 附加可能有安全性問題，但有警告的對話方塊隨即顯示。  
  
-   `FAILURE`： 附加至處理序就會失敗。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)

