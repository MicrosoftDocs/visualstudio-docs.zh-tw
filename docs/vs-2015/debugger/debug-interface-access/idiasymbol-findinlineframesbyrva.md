---
title: IDiaSymbol::findInlineFramesByRVA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: e7a6d9cb-2726-4ac7-9f38-415ad215bf9c
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f9fd6e4b8f579500552205aabd280c2d2e79e83
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149887"
---
# <a name="idiasymbolfindinlineframesbyrva"></a>IDiaSymbol::findInlineFramesByRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取列舉，可讓用戶端在指定的相對虛擬位址 (RVA) 上，逐一查看所有的內嵌框架。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT findInlineFramesByRVA (    DWORD             rva,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `rva`  
 在將位址指定為 RVA。  
  
 `ppResult`  
 擴展保存 `IDiaEnumSymbols` 物件，其中包含所抓取的框架清單。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
