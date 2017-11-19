---
title: "IDebugCookie::SetDebugCookie |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugCookie.SetDebugCookie
apilocation: pdm.dll
helpviewer_keywords: IDebugCookie::SetDebugCookie
ms.assetid: 9cba3b05-ff81-4fb0-9382-e9338cb9192d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1155b00750cfe2a91625ba0f531622f381467198
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugcookiesetdebugcookie"></a>IDebugCookie::SetDebugCookie
設定偵錯應用程式 cookie。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetDebugCookie(  
   DWORD  dwDebugAppCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwDebugAppCookie`  
 [in]Cookie 可識別偵錯應用程式。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會設定偵錯應用程式 cookie，可讓多個偵錯工具附加至處理序。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCookie 介面](../../winscript/reference/idebugcookie-interface.md)