---
title: "Idiaenumlinenumbers:: Item |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumLineNumbers::Item method
ms.assetid: 08efbeaf-22f7-49e9-96a8-bb906dfe4fd8
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee969a4451e8301bc8c110c71f6de18badfede4f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumlinenumbersitem"></a>IDiaEnumLineNumbers::Item
透過索引擷取的行號。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT Item (   
   DWORD            index,  
   IDiaLineNumber** lineNumber  
);  
```  
  
#### <a name="parameters"></a>參數  
 索引  
 [in]索引的[IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)要擷取的物件。 索引是在 0 到`count`-1，其中`count`傳回[idiaenumlinenumbers:: Get_count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md)方法。  
  
 lineNumber  
 [out]傳回[IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)物件，代表所要的行號。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)