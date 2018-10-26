---
title: 'Idiasymbol:: Get_haseha |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasEHa method
ms.assetid: cb61dfd9-fe69-461c-8185-288440454864
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 936393d3edc9273c2240787d0d1fa42ec3691748
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813462"
---
# <a name="idiasymbolgethaseha"></a>IDiaSymbol::get_hasEHa
擷取指定的函式是否包含非同步 （結構化） 例外狀況處理的旗標。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_hasEHa(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pFlag`  
 [out]會傳回`TRUE`函式有任何非同步例外狀況處理，否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不是適用於符號。  
  
## <a name="remarks"></a>備註  
 可以混合使用非同步或結構化例外狀況處理與 c + + 樣式例外狀況處理，但它需要特定的編譯器參數，/EHa，若要啟用它。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2.h|  
|版本:|DIA SDK 8.0 版|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)