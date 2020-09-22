---
title: IDiaSymbol::get_classParent | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_classParent method
ms.assetid: 99db875a-caae-4d60-ae70-64bc8a9f6fba
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e01b36dd4e4a668431d95a39a7ad14cfea475358
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839063"
---
# <a name="idiasymbolget_classparent"></a>IDiaSymbol::get_classParent
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取符號之類別父系的參考。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_classParent (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展傳回代表符號之類別父系的 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2。h|  
|版本：|DIA SDK v7.0|  
  
## <a name="remarks"></a>備註  
 可以是類別父系的符號類型會記錄在 [符號類型的類別](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)階層架構中。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [符號類型的類別階層架構](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
