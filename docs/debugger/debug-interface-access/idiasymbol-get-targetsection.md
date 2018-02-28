---
title: "Idiasymbol:: Get_targetsection |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetSection method
ms.assetid: 95382395-da41-4aa8-87f1-5b03da128565
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 192350832d2d1344cb9ae69791b526f983627545
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgettargetsection"></a>IDiaSymbol::get_targetSection
擷取 thunk 目標位址 > 一的節。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_targetSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]區段部分 thunk 目標位址。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不適用於符號。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)