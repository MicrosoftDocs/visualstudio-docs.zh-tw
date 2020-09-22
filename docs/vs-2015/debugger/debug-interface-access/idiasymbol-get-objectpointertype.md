---
title: IDiaSymbol：： get_objectPointerType |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_objectPointerType method
ms.assetid: bce193b9-67b0-4c35-96e5-6a664937322e
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1d8f5251f61b8c513c58f5165fbaecbb9d5f00f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839050"
---
# <a name="idiasymbolget_objectpointertype"></a>IDiaSymbol::get_objectPointerType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

捕獲類別方法的物件指標類型。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_objectPointerType (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展傳回 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件，代表類別方法的物件指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。  
  
## <a name="remarks"></a>備註  
 這個屬性只適用于 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md) 型別為的符號 `SymTagFunctionType` 。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
