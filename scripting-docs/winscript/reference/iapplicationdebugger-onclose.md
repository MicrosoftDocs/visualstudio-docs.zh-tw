---
title: IApplicationDebugger：： onClose |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onClose
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onClose
ms.assetid: f3d6ca9f-6697-4d02-9d1a-16e3859bf282
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e31b2a77effc729f0e7df1e36116ee554446093
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577879"
---
# <a name="iapplicationdebuggeronclose"></a>IApplicationDebugger::onClose
處理 debug 應用程式關閉事件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT onClose();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法不接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 呼叫 `IDebugApplication::Close` 時，會呼叫這個方法。  
  
## <a name="see-also"></a>請參閱  
 [IApplicationDebugger 介面](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)