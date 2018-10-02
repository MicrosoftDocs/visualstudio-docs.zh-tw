---
title: 'Idiasymbol:: Get_databytes |Microsoft Docs'
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
- IDiaSymbol::get_dataBytes method
ms.assetid: 5eb37179-20d8-44ae-a72a-405c1b0435c4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81672552bfecd824f9d969cc8b4606596d76b12a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485848"
---
# <a name="idiasymbolgetdatabytes"></a>IDiaSymbol::get_dataBytes
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[idiasymbol:: Get_databytes](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-databytes)。  
  
擷取資訊，請參閱 OEM 符號的資料位元組數。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_dataBytes (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cbData`  
 [in]保留的資料緩衝區的大小。  
  
 `pcbData`  
 [out]傳回寫入位元組數目，或者，如果`data`參數是`NULL`，傳回可用的位元組數目。  
  
 `data[]`  
 [out]會填入資料位元組的緩衝區。  
  
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



