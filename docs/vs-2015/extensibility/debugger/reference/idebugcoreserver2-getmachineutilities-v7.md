---
title: IDebugCoreServer2：： GetMachineUtilities_V7 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 131f5a5f276b3f93d2ede3d088556b6832cc3651
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839206"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個方法會取得伺服器的電腦公用程式。  
  
> [!NOTE]
> 這個方法已經過時： [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] `E_NOTIMPL` 如果呼叫這個方法) ，請不要使用 (一律會傳回。 基於歷史原因，它會保留下來。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppUtil`  
 擴展傳回 `IDebugMDMUtil2_V7` 表示電腦公用程式資訊的介面。  
  
## <a name="return-value"></a>傳回值  
 一律 `E_NOTIMPL` 會傳回，表示不會執行此方法。  
  
## <a name="remarks"></a>備註  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]`E_NOTIMPL`如果呼叫這個方法，一律會傳回。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
