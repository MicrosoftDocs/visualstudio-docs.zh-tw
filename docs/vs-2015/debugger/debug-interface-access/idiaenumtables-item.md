---
title: 'Idiaenumtables:: Item |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea80cbcda60b54f17e79e492c43058579465ad90
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491882"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[idiaenumtables:: Item](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumtables-item)。  
  
擷取透過索引或名稱的資料表。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### <a name="parameters"></a>參數  
 `index`  
 [in]索引或名稱[IDiaTable](../../debugger/debug-interface-access/idiatable.md)要擷取。 如果使用整數變數，則它必須是範圍介於 0 到`count`-1，其中`count`會傳回[idiaenumtables:: Get_count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)方法。  
  
 `table`  
 [out]傳回[IDiaTable](../../debugger/debug-interface-access/idiatable.md)物件，表示所需的資料表。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果指定的字串變數，則字串會命名特定的資料表。 中所定義，名稱應該是其中一個資料表名稱[常數 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)。  
  
## <a name="example"></a>範例  
  
```cpp#  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [Idiaenumtables:: Get_count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [常數 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)



