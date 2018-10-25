---
title: 'Idiasymbol:: Get_udtkind |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_udtKind method
ms.assetid: 4002f887-aea6-4475-b302-67c57079fe0a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1bad5019b03612195de119e5ed6a6308d1e39b6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925600"
---
# <a name="idiasymbolgetudtkind"></a>IDiaSymbol::get_udtKind
擷取的各種不同的使用者定義型別 (UDT)。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_udtKind (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回值，以從[UdtKind 列舉](../../debugger/debug-interface-access/udtkind.md)指定 UDT 類型的列舉型別： 結構、 類別或等位。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [UdtKind 列舉](../../debugger/debug-interface-access/udtkind.md)