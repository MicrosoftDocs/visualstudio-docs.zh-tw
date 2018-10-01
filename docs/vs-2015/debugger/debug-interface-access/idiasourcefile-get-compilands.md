---
title: 'Idiasourcefile:: Get_compilands |Microsoft Docs'
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
- IDiaSourceFile::get_compilands method
ms.assetid: 57deb50a-9c22-43ea-a80c-eab205997bc4
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc576a2fdd3b2a02b1b049a90bdf9f45f490f737
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497546"
---
# <a name="idiasourcefilegetcompilands"></a>IDiaSourceFile::get_compilands
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[idiasourcefile:: Get_compilands](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasourcefile-get-compilands)。  
  
擷取有參考此檔案的行號的編譯模組的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_compilands (   
   IDiaEnumSymbols** ppRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppRetVal`  
 [out]傳回[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)物件，其中包含了參考此檔案的行號的所有編譯模組的清單。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)



