---
title: IDiaSymbol：： get_container |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_container method
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b759c8fc65130c37f24e8ec03bbcebf3a52241d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839029"
---
# <a name="idiasymbolget_container"></a>IDiaSymbol::get_container
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

此函式會抓取表示此符號之父/容器的符號指標。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_container(  
   IDiaSymbol **pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展傳回 `IDiaSymbol` 包含此符號之容器相關資訊的指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 S_OK;否則，會傳回 S_FALSE 或錯誤碼。  
  
> [!NOTE]
> S_FALSE 的傳回值表示該屬性不適用於符號。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2。h|  
|版本：|DIA SDK v8.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
