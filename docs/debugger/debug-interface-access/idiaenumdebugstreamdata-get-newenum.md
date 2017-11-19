---
title: "Idiaenumdebugstreamdata:: Get__newenum |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumDebugStreamData::get__NewEnum method
ms.assetid: 023b3e31-0fc9-478d-88e8-af2ce762f322
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 98688909321974a3d2695bed8df4ae5838a9ffa5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumdebugstreamdatagetnewenum"></a>IDiaEnumDebugStreamData::get__NewEnum
擷取<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>這個列舉值的版本。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 pRetVal  
 [out]傳回`IUnknown`表示介面<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>這個列舉值的版本。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)