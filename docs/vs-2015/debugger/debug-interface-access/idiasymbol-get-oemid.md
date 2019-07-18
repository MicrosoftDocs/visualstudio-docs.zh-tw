---
title: IDiaSymbol::get_oemId | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_oemId method
ms.assetid: c472830f-c3eb-46ab-9498-cd637763d241
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 406645893803094ce0ebdd4679d9809d7645401f
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "64798064"
---
# <a name="idiasymbolgetoemid"></a>IDiaSymbol::get_oemId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取符號的原始設備製造商 (OEM) 的識別碼值。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_oemId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回唯一值，這個值可識別 OEM。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
> 傳回值為`S_FALSE`表示屬性不是適用於符號。  
  
## <a name="remarks"></a>備註  
 這個屬性只適用於具有符號[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)種`SymTagCustomType`。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
