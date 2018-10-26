---
title: 'Idiasymbol:: Get_age |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaSymbol::get_age method
ms.assetid: 60d05654-e832-4a2e-a4a7-fe9922c459fe
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 360bd975ce21c91d9fa6a414cde9272a50effd84
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853788"
---
# <a name="idiasymbolgetage"></a>IDiaSymbol::get_age
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取的.pdb 檔案的存留期值。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_age (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回.pdb 檔案的存留期的值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
 存留期不一定會對應至任何已知的時間值;它通常用來判斷是否與對應的.exe 檔案不同步的.pdb 檔案。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v7.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



