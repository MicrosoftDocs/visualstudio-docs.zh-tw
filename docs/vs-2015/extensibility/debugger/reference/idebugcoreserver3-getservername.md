---
title: IDebugCoreServer3::GetServerName | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerName
helpviewer_keywords:
- IDebugCoreServer3::GetServerName
ms.assetid: 0fc3fcf5-d6a3-4a00-bf14-458b8645714e
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 886cfbf95216064764e9f5b3e48d092d3fecc047
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445258"
---
# <a name="idebugcoreserver3getservername"></a>IDebugCoreServer3::GetServerName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

擷取伺服器的名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetServerName(  
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetServerName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrName`  
 [out]傳回伺服器的名稱。  
  
> [!NOTE]
> 呼叫端負責釋放字串。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`，否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 伺服器易記名稱時，請呼叫[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)
