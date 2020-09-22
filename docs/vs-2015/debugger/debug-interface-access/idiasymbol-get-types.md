---
title: IDiaSymbol：： get_types |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 813dcd692669d823548e52ce6bb7eccc9546de61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839211"
---
# <a name="idiasymbolget_types"></a>IDiaSymbol::get_types
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

針對這個符號抓取編譯器特定類型的陣列。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_types (   
   DWORD       cTypes,  
   DWORD*      pcTypes,  
   IDiaSymbol* types[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cTypes`  
 在保存資料的緩衝區大小。  
  
 `pcTypes`  
 擴展傳回寫入的類型數目，如果 `types` 參數為 `NULL` ，則為可用的類型總數。  
  
 `types[]`  
 擴展要填入 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件的陣列，這些物件代表此符號的所有類型。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
