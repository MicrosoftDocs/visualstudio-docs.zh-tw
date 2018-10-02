---
title: 'Idiasymbol:: Get_udtkind |Microsoft Docs'
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
- IDiaSymbol::get_udtKind method
ms.assetid: 4002f887-aea6-4475-b302-67c57079fe0a
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0a47dea769f4a11977eae5fa53cd503d16819e8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485172"
---
# <a name="idiasymbolgetudtkind"></a>IDiaSymbol::get_udtKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[idiasymbol:: Get_udtkind](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-udtkind)。  
  
擷取的各種不同的使用者定義型別 (UDT)。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_udtKind (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回值，以從[UdtKind 列舉](../../debugger/debug-interface-access/udtkind.md)指定 UDT 類型的列舉型別： 結構、 類別或等位。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [UdtKind 列舉](../../debugger/debug-interface-access/udtkind.md)



