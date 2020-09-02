---
title: IDiaSymbol：： get_isAcceleratorStubFunction |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 69f82f836be6ab91fe73af5a0febf7a39723b191
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199900"
---
# <a name="idiasymbolget_isacceleratorstubfunction"></a>IDiaSymbol::get_isAcceleratorStubFunction
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

指出符號是否對應至針對對應至呼叫之快速鍵編譯的著色器的最上層函式符號 `parallel_for_each` 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT get_isAcceleratorStubFunction(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>參數  
 `pFlag`  
 擴展的指標 `BOOL` ，指出符號是否對應至針對對應至呼叫之快速鍵所編譯之著色器的最上層函式符號 `parallel_for_each` 。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
