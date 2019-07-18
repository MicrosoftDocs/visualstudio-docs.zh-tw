---
title: IDiaSymbol::get_language | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_language method
ms.assetid: c759ad3c-1c21-4234-869b-86aa3a608a38
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd9adeba1b3ac84fa6a09d6c6f25b77e35cd429f
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "64819201"
---
# <a name="idiasymbolgetlanguage"></a>IDiaSymbol::get_language
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取來源的語言。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_language (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回值，以從[CV_CFL_LANG 列舉](../../debugger/debug-interface-access/cv-cfl-lang.md)列舉，指定來源的語言。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
> 傳回值為`S_FALSE`表示此屬性不適用於符號。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV_CFL_LANG 列舉](../../debugger/debug-interface-access/cv-cfl-lang.md)
