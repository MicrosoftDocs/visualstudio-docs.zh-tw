---
title: 'Idiasymbol:: Get_container |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_container method
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d293971cfcd0723485d4a5b21d4e431de64ddd65
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822731"
---
# <a name="idiasymbolgetcontainer"></a>IDiaSymbol::get_container
此函式會擷取變數的指標，代表父/容器的這個符號的符號。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_container(  
   IDiaSymbol **pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]將指標傳回至`IDiaSymbol`包含此符號的容器的相關資訊。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，會傳回 S_FALSE 或錯誤碼。  
  
> [!NOTE]
>  傳回值為 S_FALSE 表示屬性不是適用於符號。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2.h|  
|版本:|DIA SDK 8.0 版|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)