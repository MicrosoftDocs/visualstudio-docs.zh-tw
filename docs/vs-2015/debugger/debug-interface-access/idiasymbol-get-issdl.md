---
title: IDiaSymbol::get_isSdl |Microsoft Docs
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
ms.assetid: 6aa0e116-da75-4643-a4d7-d8e142231e21
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de68705fdf5c97bb7445852d654fee905d1087ed
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491196"
---
# <a name="idiasymbolgetissdl"></a>IDiaSymbol::get_isSdl
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDiaSymbol::get_isSdl](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-issdl)。  
  
指定是否使用 /SDL 選項編譯的模組。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT get_isSdl(  
   BOOL *pRetVal);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]指標`BOOL`，指定是否使用 /SDL 選項編譯的模組。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



