---
title: IDiaSymbol：： get_machineType |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_machineType method
ms.assetid: 30870b10-6f32-45c6-a0d7-020dea707710
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2ed70a2263cea9c6988149dacdf7269606fcdfe3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838817"
---
# <a name="idiasymbolget_machinetype"></a>IDiaSymbol::get_machineType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取目標 CPU 的型別。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_machineType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展從指定目標 CPU 類型的 [CV_CPU_TYPE_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md) 列舉傳回值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。  
  
## <a name="see-also"></a>另請參閱  
 [CV_CPU_TYPE_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
