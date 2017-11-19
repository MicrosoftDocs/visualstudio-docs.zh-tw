---
title: "ISimpleConnectionPoint::Unadvise |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ISimpleConnectionPoint.Unadvise
apilocation: pdm.dll
helpviewer_keywords: ISimpleConnectionPoint::Unadvise
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f926f206bb8a27e6265fd147909a5adb13c3543
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpointunadvise"></a>ISimpleConnectionPoint::Unadvise
終止透過先前建立諮詢連接`ISimpleConnectionPoint::Advise`。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwCookie`  
 [in]結束，傳回的連線語彙基元`ISimpleConnectionPoint::Advise`。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 當終止諮詢連接時，連接點上呼叫`Release`連線期間已儲存指標上的方法`ISimpleConnectionPoint::Advise`方法。 呼叫的反轉`AddRef`的期間執行`ISimpleConnectionPoint::Advise`當連接點呼叫通知的接收`QueryInterface`。  
  
## <a name="see-also"></a>另請參閱  
 [ISimpleConnectionPoint 介面](../../winscript/reference/isimpleconnectionpoint-interface.md)