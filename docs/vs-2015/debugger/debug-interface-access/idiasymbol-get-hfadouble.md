---
title: IDiaSymbol::get_hfaDouble | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hfaDouble method
ms.assetid: efc247b9-c16e-4fa3-89b0-901caf7b74c3
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db12f9dfb0a5a5594c08ab0cd58446cac100f7ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839028"
---
# <a name="idiasymbolget_hfadouble"></a>IDiaSymbol::get_hfaDouble
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取旗標，這個旗標會指定使用者定義型別 (UDT) 是否包含雙精度浮點數的 (HFA) 資料。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_hfaDouble(   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展 `TRUE` 如果 UDT 包含 double 類型的 HFA 資料，則傳回，否則傳回 `FALSE` 。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 標頭： Dia2。h  
  
 程式庫： diaguids .lib  
  
 DLL： msdia100.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
