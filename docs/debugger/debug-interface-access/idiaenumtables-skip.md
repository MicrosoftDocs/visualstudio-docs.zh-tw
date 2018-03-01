---
title: "Idiaenumtables:: Skip |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Skip method
ms.assetid: 5c9db956-0654-4f1a-8775-530aa980d8ec
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d2741361ddb0e7483344c5fbe123e5d4ec03588c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumtablesskip"></a>IDiaEnumTables::Skip
略過指定的數目的列舉順序中的資料表。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in]略過將列舉序列中的資料表數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`如果沒有更多的資料表以略過。  
  
## <a name="see-also"></a>請參閱  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)