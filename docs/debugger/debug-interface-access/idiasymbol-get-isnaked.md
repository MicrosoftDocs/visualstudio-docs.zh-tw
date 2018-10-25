---
title: 'Idiasymbol:: Get_isnaked |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isNaked method
ms.assetid: b16629dc-8e17-476b-9c7b-58e7277c61ed
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 32280a8b4baaf82867065898b5478c11842a33df
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915070"
---
# <a name="idiasymbolgetisnaked"></a>IDiaSymbol::get_isNaked
擷取指定函數是否有的旗標[naked](/cpp/cpp/naked-cpp)屬性 （也就是該函式具有由編譯器新增任何初構和終解程式碼）。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_isNaked(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pFlag`  
 [out]會傳回`TRUE`函式是否`naked`屬性，否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2.h|  
|版本:|DIA SDK 8.0 版|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Naked 函式呼叫](/cpp/cpp/naked-function-calls)