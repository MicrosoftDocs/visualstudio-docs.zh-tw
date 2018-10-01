---
title: 'Idiaenuminjectedsources:: Next |Microsoft Docs'
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
- IDiaEnumInjectedSources::Next method
ms.assetid: 38af80fc-748f-4b15-bff1-823db21dd4d0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 836191aacb587cc391d36e2ac052cd6f1efc3860
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497475"
---
# <a name="idiaenuminjectedsourcesnext"></a>IDiaEnumInjectedSources::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[idiaenuminjectedsources:: Next](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenuminjectedsources-next)。  
  
擷取指定的數目的列舉型別序列中的插入來源。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Next (   
   ULONG                celt,   
   IDiaInjectedSource** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 celt  
 [in]要擷取列舉值中的插入來源數目。  
  
 rgelt  
 [out]傳回的陣列[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)物件，表示所需的插入的來源。  
  
 pceltFetched  
 [out]擷取列舉值中傳回插入的來源數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`。 傳回`S_FALSE`如果有其他插入的來源。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)



