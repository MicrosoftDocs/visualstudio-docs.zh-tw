---
title: IDiaSymbol：： get_lowerBoundId |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_lowerBoundId method
ms.assetid: 12ce98e9-a225-4947-88c9-5fda39dd67e4
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 44c61f47ca5e1a1b91621cf1a3680ce51532b596
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839009"
---
# <a name="idiasymbolget_lowerboundid"></a>IDiaSymbol::get_lowerBoundId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

捕獲 FORTRAN 陣列維度下限的符號識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_lowerBoundId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展傳回代表 FORTRAN 陣列維度下限的符號的符號 ID。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。  
  
## <a name="remarks"></a>備註  
 識別碼是 DIA SDK 所建立的唯一值，會將所有符號標示為唯一的。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
