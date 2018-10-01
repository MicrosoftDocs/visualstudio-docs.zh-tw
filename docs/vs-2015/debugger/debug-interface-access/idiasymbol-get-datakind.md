---
title: 'Idiasymbol:: Get_datakind |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaSymbol::get_dataKind method
ms.assetid: 45005ad0-8b29-4cde-9d33-6bef72f6e463
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 83ec63eb7ebcc38c8a8524fbfa0e2c669919416c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491932"
---
# <a name="idiasymbolgetdatakind"></a>IDiaSymbol::get_dataKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[idiasymbol:: Get_datakind](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-datakind)。  
  
擷取資料符號的變數的分類。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_dataKind (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回值，以從[DataKind 列舉](../../debugger/debug-interface-access/datakind.md)例如指定的全域、 靜態或常數，例如資料類型的列舉類型。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不是適用於符號。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v7.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [DataKind 列舉](../../debugger/debug-interface-access/datakind.md)



