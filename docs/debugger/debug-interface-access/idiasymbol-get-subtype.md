---
title: "IDiaSymbol::get_subType |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 0b3cbf77-8f11-434a-ad60-ea9829fec6fa
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c5eb3a65e635ba4785ccf2106f596ed20bbad178
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetsubtype"></a>IDiaSymbol::get_subType
擷取的子型別。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_subType(   
   IDiaSymbol** pRetVal);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]子類型的指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)