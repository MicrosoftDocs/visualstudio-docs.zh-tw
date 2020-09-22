---
title: IDiaSymbol::get_typeId | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeId method
ms.assetid: b40be36e-10e1-463c-9c6d-21862679d29f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 39bbc4c3d032bf0864a1b8b8953252ae97341375
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839043"
---
# <a name="idiasymbolget_typeid"></a>IDiaSymbol::get_typeId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取符號的類型識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_typeId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展傳回符號的類型識別碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。  
  
## <a name="remarks"></a>備註  
 識別碼是 DIA SDK 所建立的唯一值，會將所有符號標示為唯一的。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
