---
title: IDiaLineNumber：： get_statement |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_statement method
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5ad480a3b5d3ed892fc56fec2c882638f986810
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68165686"
---
# <a name="idialinenumberget_statement"></a>IDiaLineNumber::get_statement
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取旗標，指出這行資訊描述程式來源中語句的開頭，而不是運算式。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_statement (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展 `TRUE` 如果這行資訊描述程式來源中語句的開頭，則傳回。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援這個屬性，則傳回。 否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 語句可以跨多行。 這個方法會指出相關行號是否標記這類多行語句的開頭。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
