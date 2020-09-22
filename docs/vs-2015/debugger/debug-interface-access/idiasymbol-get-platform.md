---
title: IDiaSymbol：： get_platform |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_platform method
ms.assetid: dff1c1eb-bcb2-4275-bb07-f2fdc076d6fb
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c44603a767903e71103107fab6f8f041e7946902
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838805"
---
# <a name="idiasymbolget_platform"></a>IDiaSymbol::get_platform
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取已編譯編譯單位的平臺類型。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_platform (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展傳回 [CV_CPU_TYPE_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md) 列舉中的值，這個值會指定編譯編譯單位的平臺類型。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV_CPU_TYPE_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md)
