---
title: IDiaSymbol::get_hasEH | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasEH method
ms.assetid: 9a4952d8-9fa7-4798-b48c-fe4357648276
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e4badf13f21bae028ee782d23bc26b1c1348ebeb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839004"
---
# <a name="idiasymbolget_haseh"></a>IDiaSymbol::get_hasEH
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取旗標，這個旗標會指定函數是否包含任何非受控 c + + 樣式例外狀況處理 (例如 try/catch 區塊) 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT get_hasEH(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pFlag`  
 擴展 `TRUE` 如果函式具有任何 c + + 樣式例外狀況處理，則傳回，否則傳回 `FALSE` 。  
  
## <a name="return-value"></a>傳回值  
 如果成功， `S_OK` 則傳回; 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2。h|  
|版本：|DIA SDK v8.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
