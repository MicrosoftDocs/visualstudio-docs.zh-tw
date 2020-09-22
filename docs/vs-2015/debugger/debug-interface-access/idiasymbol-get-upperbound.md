---
title: IDiaSymbol：： get_upperBound |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_upperBound method
ms.assetid: a77dcafa-ea3f-45da-826d-8f9b4489a03f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f965cddfa9d5d071bd08e4473cff49c82703d7ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838954"
---
# <a name="idiasymbolget_upperbound"></a>IDiaSymbol::get_upperBound
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取代表 FORTRAN 陣列維度上限的符號。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_upperBound (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展傳回 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件，這個物件表示 FORTRAN 陣列維度的上限。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
