---
title: IDebugApplication::StartDebugSession | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.StartDebugSession
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::StartDebugSession
ms.assetid: 737f8424-bbcf-473f-9cf1-6601b9aa250d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a42fe61d67eedbe6f69350c7b5ec17726f43486e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990685"
---
# <a name="idebugapplicationstartdebugsession"></a>IDebugApplication::StartDebugSession
啟動預設的偵錯工具整合式的開發環境 (IDE)，並將偵錯工作階段附加至這個應用程式而言，如果其中一個尚未附加。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT StartDebugSession();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法用來實作-just-in-time 偵錯。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)