---
title: IDiaSymbol::findSymbolsForAcceleratorPointerTag |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: fb66852c-c5f7-4140-b9fe-20cb4e51a9fe
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54f945dcb9f043c48014921680c95669eee33673
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "68149860"
---
# <a name="idiasymbolfindsymbolsforacceleratorpointertag"></a>IDiaSymbol::findSymbolsForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

傳回的加速器指標中的標記數目C++AMP 虛設常式的函式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT findSymbolsForAccleratorPointerTag (   
   DWORD             tagValue,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### <a name="parameters"></a>參數  
 `tagValue`  
 [in]位於 pointee 符號記錄指標標記值。  
  
 `ppResult`  
 [out]指標`IDiaEnumSymbols`初始化與結果的介面指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
