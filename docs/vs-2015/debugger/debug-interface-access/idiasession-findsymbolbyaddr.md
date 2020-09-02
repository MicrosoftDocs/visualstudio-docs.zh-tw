---
title: IDiaSession::findSymbolByAddr | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByAddr method
ms.assetid: c130abc5-4d0a-4d2d-8286-94fde36ddd4a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 40cddc1c4088ca51791a6778a436e2f1161444ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68165512"
---
# <a name="idiasessionfindsymbolbyaddr"></a>IDiaSession::findSymbolByAddr
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取指定的符號類型，其中包含或最接近指定的位址。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT findSymbolByAddr (   
   DWORD        isect,  
   DWORD        offset,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>參數  
 `isect`  
 在指定位址的區段元件。  
  
 `offset`  
 在指定位址的位移元件。  
  
 `symtag`  
 在要尋找的符號類型。 值取自 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md) 列舉。  
  
 `ppSymbol`  
 擴展傳回代表已抓取符號的 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="example"></a>範例  
  
```cpp#  
IDiaSymbol* pFunc;  
pSession->findSymbolByAddr( isect, offset, SymTagFunction, &pFunc );  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
