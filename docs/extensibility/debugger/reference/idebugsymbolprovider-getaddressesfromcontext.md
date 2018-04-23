---
title: IDebugSymbolProvider::GetAddressesFromContext |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 09bc0d4fc0a723c259e2897b95abbd8611b10c7d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
這個方法會將文件內容對應至的偵錯位址陣列。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetAddressesFromContext(   
   IDebugDocumentContext2* pDocContext,  
   BOOL                    fStatmentOnly,  
   IEnumDebugAddresses**   ppEnumBegAddresses,  
   IEnumDebugAddresses**   ppEnumEndAddresses  
);  
```  
  
```csharp  
int GetAddressesFromContext(  
   IDebugDocumentContext2  pDocContext,  
   bool                    fStatmentOnly,  
   out IEnumDebugAddresses ppEnumBegAddresses,  
   out IEnumDebugAddresses ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pDocContext`  
 [in]文件內容。  
  
 `fStatmentOnly`  
 [in]如果為 TRUE，則會限制位址給單一陳述式的偵錯。  
  
 `ppEnumBegAddresses`  
 [out]傳回列舉，此陳述式或列相關聯之開始偵錯位址。  
  
 `ppEnumEndAddresses`  
 [out]傳回[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)結束此陳述式或列相關聯的偵錯地址的列舉值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 文件內容通常表示原始程式行的範圍。 這個方法提供的開始和結束偵錯位址與這行關聯。 有些語言允許跨越多個線路或包含多個陳述式的陳述式。 這個方法提供的旗標，以限制在單一陳述式的偵錯位址。  
  
 很可能在單一陳述式具有多個偵錯位址，如同範本的情況。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)