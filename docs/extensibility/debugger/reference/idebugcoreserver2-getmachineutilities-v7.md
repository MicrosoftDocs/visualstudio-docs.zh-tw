---
title: IDebugCoreServer2::GetMachineUtilities_V7 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 265c5b414c53fb6dfe43f63c1016204b8ff02c81
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908661"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
這個方法會取得伺服器的機器的公用程式。  
  
> [!NOTE]
>  這個方法已經過時： 請勿使用 ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]一律會傳回`E_NOTIMPL`如果在呼叫此方法)。 它會保留歷程記錄的原因。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppUtil`  
 [out]傳回`IDebugMDMUtil2_V7`表示機器的公用程式資訊的介面。  
  
## <a name="return-value"></a>傳回值  
 一律會傳回`E_NOTIMPL`，指出，該方法尚未實作。  
  
## <a name="remarks"></a>備註  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 一律會傳回`E_NOTIMPL`如果呼叫這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)