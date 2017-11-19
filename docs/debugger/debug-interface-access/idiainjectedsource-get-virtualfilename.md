---
title: "Idiainjectedsource:: Get_virtualfilename |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaInjectedSource::get_virtualFilename method
ms.assetid: b9977075-8fd1-4b11-bfff-d87e9f2586dc
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab52f6dee7152837c17508aac65eeab501c7f0c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiainjectedsourcegetvirtualfilename"></a>IDiaInjectedSource::get_virtualFilename
擷取非檔案原始碼; 提供的名稱也就是已插入的程式碼。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_virtualFilename (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回提供給插入非檔案原始碼的名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)