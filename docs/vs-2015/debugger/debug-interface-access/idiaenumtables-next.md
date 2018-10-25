---
title: 'Idiaenumtables:: Next |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Next method
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b566d40e34b38eb5f1d2a10afc1df50e4f5199cb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896311"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取指定的數目的列舉型別序列中的資料表。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Next (   
   ULONG       celt,  
   IDiaTable** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in]要擷取列舉值中的資料表數目。  
  
 `rgelt`  
 [out]陣列，其中是要在以填滿[IDiaTable](../../debugger/debug-interface-access/idiatable.md)所需的資料表表示的物件。  
  
 `pceltFetched`  
 [out]擷取列舉值中傳回資料表的數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`。 傳回`S_FALSE`如果沒有更多的資料表。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)



