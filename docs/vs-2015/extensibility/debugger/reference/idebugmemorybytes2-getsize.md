---
title: IDebugMemoryBytes2::GetSize |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMemoryBytes2::GetSize
helpviewer_keywords:
- IDebugMemoryBytes2::GetSize method
- GetSize method
ms.assetid: dae64c5f-5b54-40c3-b32f-ec3b16c093f7
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2fa4e9de3063c67939a14f693307ebd19481d551
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843612"
---
# <a name="idebugmemorybytes2getsize"></a>IDebugMemoryBytes2::GetSize
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

擷取的大小，以位元組為單位所表示的記憶體[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)物件。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetSize(   
   UINT64* pqwSize  
);  
```  
  
```csharp  
int GetSize(  
   out ulong pqwSize  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pqwSize`  
 [out]傳回大小，以位元組為單位的記憶體空間。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)

