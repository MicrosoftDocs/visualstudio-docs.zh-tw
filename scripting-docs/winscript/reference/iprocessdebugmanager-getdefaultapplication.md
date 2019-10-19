---
title: IProcessDebugManager：： GetDefaultApplication |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.GetDefaultApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::GetDefaultApplication
ms.assetid: 6c991faa-ea40-4d18-a1b8-6e7d0de6dd43
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3532177c32e0d7eb0b7a67a445845cee753d316
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576803"
---
# <a name="iprocessdebugmanagergetdefaultapplication"></a>IProcessDebugManager::GetDefaultApplication
傳回目前進程的預設應用程式物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetDefaultApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppda`  
 脫銷這個應用程式的 debug 應用程式物件。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會建立新的 debug 應用程式物件，並視需要將它新增至執行中的應用程式清單。  
  
 如果語言引擎在不提供應用程式的主機上執行，則應該使用 `GetDefaultApplication` 方法所指定的應用程式。  
  
## <a name="see-also"></a>請參閱  
 [IProcessDebugManager 介面](../../winscript/reference/iprocessdebugmanager-interface.md)