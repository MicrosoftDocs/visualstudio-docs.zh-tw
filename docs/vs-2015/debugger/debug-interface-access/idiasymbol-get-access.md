---
title: 'Idiasymbol:: Get_access |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_access method
ms.assetid: 908976ae-95c4-4020-89c9-de137f727f98
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 806e9fd06611e2cb30829b294222870b9252c35b
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "64808094"
---
# <a name="idiasymbolgetaccess"></a>IDiaSymbol::get_access
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取的類別成員的存取修飾詞。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_access (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回值，以從[CV_access_e 列舉](../../debugger/debug-interface-access/cv-access-e.md)列舉，指定類別成員的存取修飾詞。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
> 傳回值為`S_FALSE`表示屬性不是適用於符號。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v7.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV_access_e 列舉](../../debugger/debug-interface-access/cv-access-e.md)
