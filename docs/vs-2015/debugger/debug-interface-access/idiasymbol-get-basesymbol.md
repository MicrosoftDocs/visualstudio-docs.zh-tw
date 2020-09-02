---
title: IDiaSymbol：： get_baseSymbol |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: cabb5a18-bda7-47e8-9e46-5f4718579fc9
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9458f4e848f750d4a7eb11a866a2730f331e7244
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149806"
---
# <a name="idiasymbolget_basesymbol"></a>IDiaSymbol::get_baseSymbol
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取指標所依據的符號。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT get_baseSymbol(   
   IDiaSymbol** pRetVal);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展指標所依據的符號指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)
