---
title: IDiaSymbol::get_virtual | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtual method
ms.assetid: 97e3ad51-8ef3-4446-ab33-3cb34a21b7a0
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dd085926c25bd15b321222ce36a0d61a5f650649
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838913"
---
# <a name="idiasymbolget_virtual"></a>IDiaSymbol::get_virtual
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取指定函數是否為虛擬的旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_virtual (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展 `TRUE` 如果函數是虛擬的，則傳回，否則傳回 `FALSE` 。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
