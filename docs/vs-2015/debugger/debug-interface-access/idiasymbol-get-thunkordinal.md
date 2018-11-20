---
title: 'Idiasymbol:: Get_thunkordinal |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 899cdbc261385e2e392ed70dd998e4f8c116a14f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737129"
---
# <a name="idiasymbolgetthunkordinal"></a>IDiaSymbol::get_thunkOrdinal
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取函式的 thunk 類型。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回值，以從[THUNK_ORDINAL 列舉](../../debugger/debug-interface-access/thunk-ordinal.md)列舉，指定函式的 thunk 類型。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
 這個屬性就有效才做為符號[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)的值`SymTagThunk`。  
  
 「 Thunk 」 是一種轉換的 32 位元記憶體位址空間 （也就是一般的位址空間） 和 （又稱為分段的位址空間） 的 16 位元位址空間的程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [THUNK_ORDINAL 列舉](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)



