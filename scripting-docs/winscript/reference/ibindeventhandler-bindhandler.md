---
title: IBindEventHandler：： BindHandler |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IBindEventHandler.BindHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IBindEventHandler::BindHandler
ms.assetid: 87909828-2224-4bb1-a6c9-dfe715ac4c9b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 160020832509c9fb2aa95c095148127228a92e17
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572566"
---
# <a name="ibindeventhandlerbindhandler"></a>IBindEventHandler::BindHandler
將事件系結至物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT BindHandler(  
   LPCOLESTR   pstrEvent,  
   IDispatch*  pdisp  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstrEvent`  
 在指定要處理的事件。  
  
 `pdisp`  
 在指定要處理事件的物件。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會將事件系結至物件。  
  
## <a name="see-also"></a>請參閱  
 [IBindEventHandler 介面](../../winscript/reference/ibindeventhandler-interface.md)