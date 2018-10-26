---
title: 'Idiasymbol:: Get_virtual |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtual method
ms.assetid: 97e3ad51-8ef3-4446-ab33-3cb34a21b7a0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfd5542895111dc9e394a20ad02f27f56e894308
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49871702"
---
# <a name="idiasymbolgetvirtual"></a>IDiaSymbol::get_virtual
擷取指定函數是否為虛擬的旗標。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_virtual (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]會傳回`TRUE`函式是虛擬，否則為，如果傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)