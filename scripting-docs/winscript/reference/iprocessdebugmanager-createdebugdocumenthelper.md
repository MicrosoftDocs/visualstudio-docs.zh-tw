---
title: IProcessDebugManager：： CreateDebugDocumentHelper |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.CreateDebugDocumentHelper
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::CreateDebugDocumentHelper
ms.assetid: d644e192-1bcc-4768-a91e-239cd920adcd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a009fa5174ab897116c02b91e376e2dc41d67600
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577098"
---
# <a name="iprocessdebugmanagercreatedebugdocumenthelper"></a>IProcessDebugManager::CreateDebugDocumentHelper
為此應用程式建立新的 debug 檔 helper。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CreateDebugDocumentHelper(  
   IUnknown*               punkOuter,  
   IDebugDocumentHelper**  pddh  
);  
```  
  
#### <a name="parameters"></a>參數  
 `punkOuter`  
 在如果要匯總傳回的物件，`punkOuter` 是控制 `IUnknown` 的介面指標。 否則，它會是 null 指標。  
  
 `pddh`  
 脫銷此應用程式的 debug 檔 helper 物件。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會為此應用程式建立新的 debug 檔 helper。  
  
## <a name="see-also"></a>請參閱  
 [IProcessDebugManager 介面](../../winscript/reference/iprocessdebugmanager-interface.md)