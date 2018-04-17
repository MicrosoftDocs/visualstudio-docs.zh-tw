---
title: IDebugSymbolProvider::GetAddressesFromPosition |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: dd01516386d68d3a17d56061f7fcd27109212b6b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
這個方法會對應到陣列的文件位置的偵錯的位址。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetAddressesFromPosition(   
   IDebugDocumentPosition2* pDocPos,  
   BOOL                     fStatmentOnly,  
   IEnumDebugAddresses**    ppEnumBegAddresses,  
   IEnumDebugAddresses**    ppEnumEndAddresses  
);  
```  
  
```csharp  
int GetAddressesFromPosition(   
   IDebugDocumentPosition2  pDocPos,  
   bool                     fStatmentOnly,  
   out IEnumDebugAddresses  ppEnumBegAddresses,  
   out IEnumDebugAddresses  ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pDocPos`  
 [in]文件位置。  
  
 `fStatmentOnly`  
 [in]如果為 TRUE，則會限制位址給單一陳述式的偵錯。  
  
 `ppEnumBegAddresses`  
 [out]傳回列舉，此陳述式或列相關聯之開始偵錯位址。  
  
 `ppEnumEndAddresses`  
 [out]傳回[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)結束此陳述式或列相關聯的偵錯地址的列舉值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 文件位置通常表示原始程式行的範圍。 這個方法提供的開始和結束偵錯位址與這行關聯。 有些語言允許跨越多個線路或包含多個陳述式的陳述式。 這個方法提供的旗標，以限制在單一陳述式的偵錯位址。  
  
 很可能在單一陳述式具有多個偵錯位址，如同範本的情況。  
  
## <a name="see-also"></a>請參閱  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)