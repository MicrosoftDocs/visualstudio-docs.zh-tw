---
title: IDiaSession::findSymbolsByRVAForAcceleratorPointerTag |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad2a0656b03fb057b631319e922a83605fa62a6e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53859460"
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
指定對應的標記值，這個方法會傳回包含符號的列舉型別函式中指定的父加速器虛設常式在指定的相對虛擬位址。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   DWORD                 rva,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `parent`  
 [in]`IDiaSymbol` ，其對應於要搜尋的加速器虛設常式函式。  
  
 `tagValue`  
 [in]指標的標記值。  
  
 `rva`  
 [in]相對虛擬位址。  
  
 `ppResult`  
 [out]指標`IDiaEnumSymbols`初始化與結果的介面指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 只有在呼叫這個方法`IDiaSymbol`加速器虛設常式函式對應的介面。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)