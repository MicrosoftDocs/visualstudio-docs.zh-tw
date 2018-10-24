---
title: 'Idiaenumdebugstreamdata:: Next |Microsoft Docs'
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
- IDiaEnumDebugStreamData::Next method
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6e361ee151ff76334e8cf3a3c4cb9216f9ff422
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920335"
---
# <a name="idiaenumdebugstreamdatanext"></a>IDiaEnumDebugStreamData::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取指定的列舉順序中的記錄數。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Next (   
   ULONG  celt,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[],  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 celt  
 [in]要擷取的記錄數目。  
  
 cbData  
 [in]資料緩衝區，以位元組為單位的大小。  
  
 pcbData  
 [out]傳回動作傳回的位元組的數目。 如果`data`是 NULL，則`pcbData`所有要求的記錄包含的可用資料的位元組總數。  
  
 [資料]  
 [out]要填滿偵錯資料流記錄資料的緩衝區。  
  
 pceltFetched  
 [in、 out]傳回的記錄數目`data`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`。 傳回`S_FALSE`如果沒有更多的記錄。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)



