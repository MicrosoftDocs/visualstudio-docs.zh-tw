---
title: IMachineDebugManagerCookie：： EnumApplications |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerCookie.EnumApplications
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerCookie::EnumApplications
ms.assetid: 03f863cf-fa7f-4ec4-b1a1-1ae0ad296c39
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e01af108e2e417976a61038d7ed3952cb33742c6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573895"
---
# <a name="imachinedebugmanagercookieenumapplications"></a>IMachineDebugManagerCookie::EnumApplications
傳回目前正在執行之應用程式清單的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT EnumApplications(  
   IEnumRemoteDebugApplications**  ppeda  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppeda`  
 脫銷包含目前正在執行之應用程式清單的列舉值。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回目前正在執行之應用程式清單的列舉值。 偵錯工具 IDE 會使用這個方法來顯示和附加應用程式，以進行調試。  
  
## <a name="see-also"></a>請參閱  
 [IMachineDebugManagerCookie 介面](../../winscript/reference/imachinedebugmanagercookie-interface.md)