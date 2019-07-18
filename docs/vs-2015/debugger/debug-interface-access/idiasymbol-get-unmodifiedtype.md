---
title: IDiaSymbol::get_unmodifiedType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_unmodifiedType method
ms.assetid: bf914dc0-ff84-4f5d-9f75-1733b17f3be0
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b6ab6bd7fc756e648955efa6db5ba9c186952d84
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "64806573"
---
# <a name="idiasymbolgetunmodifiedtype"></a>IDiaSymbol::get_unmodifiedType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取這個符號的原始類型。 使用時機[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)設為型別。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_unmodifiedType(   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，表示這個符號的原始型別。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
> 傳回值為`S_FALSE`表示此屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
 目前的類型是傳回的原始型別所做的修改。 符號的原始型別可以先取得符號的類型，和接著詢問所傳回的原始類型的類型來判斷。 請注意一些符號可能不會有原始類型的修改的類型。  
  
## <a name="requirements"></a>需求  
 標頭：dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
