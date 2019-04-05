---
title: IDiaSectionContrib::get_discardable | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_discardable method
ms.assetid: 30ca88d4-3198-4b0f-b30e-2e54b3607fe9
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2de3b8af5cebada172f139066579effcb437b0b0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944412"
---
# <a name="idiasectioncontribgetdiscardable"></a>IDiaSectionContrib::get_discardable
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取旗標，指出是否可以捨棄一節。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_discardable (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]會傳回`TRUE`可從記憶體捨棄一節，視需要; 否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
