---
title: IDebugSymbolProviderDirect::GetMethodFromAddress |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2b164e7e317da54f6ea22131e923c55901acec49
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
擷取在指定的偵錯位址之方法的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMethodFromAddress(  
   IDebugAddress* pAddress,  
   GUID*          pGuid,  
   DWORD*         pAppID,  
   _mdToken*      pTokenClass,  
   _mdToken*      pTokenMethod,  
   DWORD*         pdwOffset,  
   DWORD*         pdwVersion  
);  
```  
  
```csharp  
int GetMethodFromAddress(  
   IDebugAddress pAddress,  
   out Guid      pGuid,  
   out uint      pAppID,  
   out uint      pTokenClass,  
   out uint      pTokenMethod,  
   out uint      pdwOffset,  
   out uint      pdwVersion  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pAddress`  
 [in]偵錯所代表的位址[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面。  
  
 `pGuid`  
 [out]模組的唯一識別碼。  
  
 `pAppID`  
 [out]應用程式定義域的識別項。  
  
 `pTokenClass`  
 [out]語彙基元，代表包含的類別。  
  
 `pTokenMethod`  
 [out]語彙基元所代表的模組。  
  
 `pdwOffset`  
 [out]以位元組為單位，從開頭的位移`pAddress`參數。  
  
 `pdwVersion`  
 [out]方法的版本號碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)