---
title: IDiaSectionContrib::get_code16bit |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_code16bit method
ms.assetid: 8cde8fc5-9546-4f82-b4a8-afd0d835039e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6057f6d6bb217908e3980a6a3fdd42584431ab55
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858416"
---
# <a name="idiasectioncontribgetcode16bit"></a>IDiaSectionContrib::get_code16bit
擷取指出區段是否包含 16 位元程式碼的旗標。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_code16bit(  
   BOOL *pRetVal  
};  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]會傳回`TRUE`一節中的程式碼是 16 位元; 否則如果傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法只會指出，程式碼是否為 16 位元的位置。 如果程式碼不是 16 位元，它可能是任何其他動作，例如 32 位元或 64 位元的程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)