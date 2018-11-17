---
title: 'Idialinenumber:: Get_compiland |Microsoft Docs'
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
- IDiaLineNumber::get_compiland method
ms.assetid: c476d0b8-c473-47eb-96f5-c4e8f577b1c9
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efe34684efc185172bf5545839686bf1bc277975
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807425"
---
# <a name="idialinenumbergetcompiland"></a>IDiaLineNumber::get_compiland
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取提供映像文字的位元組數將編譯模組符號的參考。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_compiland (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 pRetVal  
 [out]傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)提供映像文字的位元組數將編譯模組的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)



