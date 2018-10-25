---
title: 'Idiaenumstackframes:: Next |Microsoft Docs'
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
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f0ba329fcd257f91aaddcabc12e844b4a3726b1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899301"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取列舉型別序列中的堆疊框架項目指定的數目。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Next(   
   ULONG             celt,  
   IDiaStackFrame**  rgelt,  
   ULONG*            pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 celt  
 [in]要擷取列舉值中的 stackframe 元素數目。  
  
 rgelt  
 [out]陣列，是要填入所要求[IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)物件。  
  
 pceltFetched  
 [out]擷取列舉值中傳回的堆疊框架項目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`。 傳回`S_FALSE`有沒有更多的堆疊框架。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)



