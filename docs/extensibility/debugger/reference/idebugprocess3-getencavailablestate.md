---
title: IDebugProcess3::GetENCAvailableState |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::GetENCAvailableState
helpviewer_keywords:
- IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7f70f685fe8792f698dcc397b2f3fc9ccb6de8dc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49927719"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
這個方法會取得目前的編輯後繼續狀態的程序。 自訂連接埠供應商應該一律傳回`E_NOTIMPL`。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetENCAvailableState(  
   EncUnavailableReason* pReason  
);  
```  
  
```csharp  
int GetENCAvailableState(  
   EncUnavailableReason[] pReason  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pReason`  
 [out]值，以從[EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)列舉型別。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`，否則會傳回錯誤碼。  
  
> [!NOTE]
>  自訂連接埠供應商應該一律傳回`E_NOTIMPL`。  
  
## <a name="remarks"></a>備註  
 此狀態可能會受到[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)