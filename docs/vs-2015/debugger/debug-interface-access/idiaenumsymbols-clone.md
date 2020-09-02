---
title: IDiaEnumSymbols：： Clone |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Clone method
ms.assetid: 5c542025-98cf-4307-901f-b9430f780cf0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b3643e2bca1e5e3a14ec81c1342f58408554efe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423891"
---
# <a name="idiaenumsymbolsclone"></a>IDiaEnumSymbols::Clone
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

建立包含與目前列舉值相同列舉狀態的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumSymbols** ppenum  
);  
```  
  
#### <a name="parameters"></a>參數  
 ppenum  
 擴展傳回包含重複列舉值的 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) 物件。 符號不會重複，只會複製列舉值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
