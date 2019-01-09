---
title: IRemoteDebugApplication::ConnectDebugger |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ConnectDebugger
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ConnectDebugger
ms.assetid: ded94101-7efe-466f-aa70-b3e30a38c4d8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e6db85ab30d04ebaf24ec0e955aab529ff8799d
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088851"
---
# <a name="iremotedebugapplicationconnectdebugger"></a>IRemoteDebugApplication::ConnectDebugger
連接到這個應用程式的偵錯工具。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT ConnectDebugger(  
   IApplicationDebugger*  pad  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pad`  
 [in]偵錯工具附加至這個應用程式。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|偵錯工具已經連接到此應用程式。|  
  
## <a name="remarks"></a>備註  
 應用程式可以有一次連接的只有一個偵錯工具。 如果偵錯工具已連接，這個方法將會失敗。  
  
## <a name="see-also"></a>另請參閱  
 [IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)   
 [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)