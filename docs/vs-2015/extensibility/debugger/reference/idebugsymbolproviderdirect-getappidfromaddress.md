---
title: IDebugSymbolProviderDirect::GetAppIDFromAddress | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetAppIDFromAddress
- GetAppIDFromAddress
ms.assetid: d76a0f36-79c4-4c58-9db3-880b00d11610
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa46f758e3f5b9379232b26da22c5ba234413d72
ms.sourcegitcommit: 0cd282a7584b9bfd4df7882f8fdf3ad8a270e219
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2019
ms.locfileid: "62421340"
---
# <a name="idebugsymbolproviderdirectgetappidfromaddress"></a>IDebugSymbolProviderDirect::GetAppIDFromAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

擷取指定的偵錯位址的應用程式網域識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetAppIDFromAddress(  
   IDebugAddress* pAddress,  
   DWORD*         pAppID  
);  
```  
  
```csharp  
int GetAppIDFromAddress(  
   IDebugAddress pAddress,  
   out uint      pAppID  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pAddress`  
 [in]偵錯所表示的地址[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面。  
  
 `pAppID`  
 [out]應用程式定義域的識別項。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
