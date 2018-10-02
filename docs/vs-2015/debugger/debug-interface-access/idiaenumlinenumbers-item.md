---
title: 'Idiaenumlinenumbers:: Item |Microsoft Docs'
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
- IDiaEnumLineNumbers::Item method
ms.assetid: 08efbeaf-22f7-49e9-96a8-bb906dfe4fd8
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a74fac7ae3a75d88b70360d36dafe5c4d85cb72
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485121"
---
# <a name="idiaenumlinenumbersitem"></a>IDiaEnumLineNumbers::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[idiaenumlinenumbers:: Item](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumlinenumbers-item)。  
  
透過索引中擷取的行號。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Item (   
   DWORD            index,  
   IDiaLineNumber** lineNumber  
);  
```  
  
#### <a name="parameters"></a>參數  
 索引  
 [in]索引[IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)要擷取的物件。 索引是在範圍介於 0 到`count`-1，其中`count`會傳回[idiaenumlinenumbers:: Get_count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md)方法。  
  
 LineNumber  
 [out]傳回[IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)物件，代表所要的行號。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)



