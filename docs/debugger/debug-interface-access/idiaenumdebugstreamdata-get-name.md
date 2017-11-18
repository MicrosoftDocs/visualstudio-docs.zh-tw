---
title: "Idiaenumdebugstreamdata:: Get_name |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumDebugStreamData::get_Name method
ms.assetid: e6cf2bed-ee2b-4122-886d-c20d93df7ff2
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ebf4e56004bf684edd46cccf977e91fe5ba8a7b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumdebugstreamdatagetname"></a>IDiaEnumDebugStreamData::get_name
擷取偵錯資料流的名稱。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_Name (   
   BSTR * pRetVal  
)  
```  
  
#### <a name="parameters"></a>參數  
 pRetVal  
 [out]傳回偵錯資料流的名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)