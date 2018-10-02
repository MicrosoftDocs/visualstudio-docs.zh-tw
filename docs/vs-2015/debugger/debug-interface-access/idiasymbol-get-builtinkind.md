---
title: IDiaSymbol::get_builtInKind |Microsoft Docs
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
ms.assetid: 953e6dba-582e-4b76-b736-898b92e5693e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4f1a3ce7007974ca7edf48c294368917c88bfdd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486809"
---
# <a name="idiasymbolgetbuiltinkind"></a>IDiaSymbol::get_builtInKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDiaSymbol::get_builtInKind](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-builtinkind)。  
  
擷取 HLSL 型別的內建類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT get_buildInKind(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]指標`DWORD`保存內建的 HLSL 型別。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



