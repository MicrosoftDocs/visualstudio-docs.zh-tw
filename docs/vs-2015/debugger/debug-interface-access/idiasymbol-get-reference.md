---
title: IDiaSymbol：： get_reference |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_reference method
ms.assetid: 6a97cb74-6a14-41fd-8e24-2a42d7a1e529
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b76dad15f715aa624880d10b3391107c1c2d8724
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839162"
---
# <a name="idiasymbolget_reference"></a>IDiaSymbol::get_reference
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取旗標，這個旗標會指定指標型別是否為參考。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_reference (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展 `TRUE` 如果指標類型是參考，則傳回，否則傳回 `FALSE` 。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
