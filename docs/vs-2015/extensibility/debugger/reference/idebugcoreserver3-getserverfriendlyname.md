---
title: IDebugCoreServer3::GetServerFriendlyName | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a29a8553a128903ed6da037f605a14bcb1db367c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940976"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

擷取伺服器的易記名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetServerFriendlyName(  
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetServerFriendlyName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrName`  
 [out]傳回伺服器的易記名稱。  
  
> [!NOTE]
>  呼叫端負責釋放字串。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`，否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 若為使用者啟動的伺服器，這個方法所傳回的名稱會是伺服器的完整名稱。 若為自動啟動伺服器，名稱會是該機器的伺服器上執行。  
  
 機器導向名稱時，請呼叫[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)
