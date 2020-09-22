---
title: IDiaSymbol：： get_sealed |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_sealed method
ms.assetid: cd1fef1f-47de-47c7-885f-f6f0a9a07d8c
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5a25bf67daa11e6bf9464cc29d696bb7c243b617
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838919"
---
# <a name="idiasymbolget_sealed"></a>IDiaSymbol::get_sealed
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取指定類別或方法是否為密封的旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_sealed(   
   BOOL* pRetVal)  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展 `TRUE` 如果類別或方法是密封的，則傳回，否則傳回 `FALSE` 。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。  
  
## <a name="remarks"></a>備註  
 密封類別不能當做基底類別使用。 密封的方法不能是覆寫。  
  
## <a name="requirements"></a>需求  
 標頭： Dia2。h  
  
 程式庫： diaguids .lib  
  
 DLL： msdia100.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
