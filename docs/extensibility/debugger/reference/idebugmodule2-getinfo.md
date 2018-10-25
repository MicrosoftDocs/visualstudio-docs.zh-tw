---
title: IDebugModule2::GetInfo |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 859a85b51e83d438ea4051e2506c2dc0696768b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820677"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
取得此模組的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetInfo(   
   MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO*       pInfo  
);  
```  
  
```cpp  
int GetInfo(   
   enum_MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO[]           pInfo  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwFields`  
 [in]從旗標的組合[MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)列舉，指定哪些欄位`pInfo`要填寫。  
  
 `pInfo`  
 [in、 out]A [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)結構，其中會填入模組的描述。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)結構包含模組中所顯示的名稱**模組**視窗。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)