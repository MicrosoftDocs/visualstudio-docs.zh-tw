---
title: IDebugApplication::StepOutComplete |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.StepOutComplete
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::StepOutComplete
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1798d347fff11a49b945519fd20c370eca75d590
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089917"
---
# <a name="idebugapplicationstepoutcomplete"></a>IDebugApplication::StepOutComplete
通知程序的偵錯管理員在單一步驟模式中的語言引擎即將返回其呼叫端。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT StepOutComplete();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 語言引擎會呼叫這個方法在單一步驟模式中傳回給其呼叫端之前。 處理序偵錯管理員會使用這個機會來通知所有其他他們應該在第一次機會中斷的指令碼引擎。 這項技術是實作模式的跨語言步驟。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)