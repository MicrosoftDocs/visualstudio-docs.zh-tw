---
title: IDiaSymbol::get_registerId | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 580637cf1058c8bfbd10ac7812e59c802830d95e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839083"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

當 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md) 設定為時，抓取位置的註冊指示項 `LocIsEnregistered` 。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展傳回位置的註冊指示項。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
 如果符號是相對於暫存器，亦即，如果符號的 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md) 設定為 `LocIsRegRel` ，請使用 `get_registerId` 方法，然後呼叫 [IDiaSymbol：： get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) 方法，以取得符號所在位置之暫存器的位移。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)
