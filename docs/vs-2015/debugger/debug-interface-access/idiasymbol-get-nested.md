---
title: IDiaSymbol：： get_nested |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_nested method
ms.assetid: 6ae46d43-8486-48d6-a6f2-d73ebf4023e3
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f21a47c677d44e097c84c2f66ac06bd7e1a957dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838839"
---
# <a name="idiasymbolget_nested"></a>IDiaSymbol::get_nested
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取旗標，這個旗標會指定使用者定義資料類型是否為嵌套的。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_nested (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展 `TRUE` 如果使用者定義資料型別是嵌套的，則傳回，否則傳回 `FALSE` 。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
