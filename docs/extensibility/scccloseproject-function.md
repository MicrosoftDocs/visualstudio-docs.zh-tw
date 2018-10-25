---
title: SccCloseProject 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: abb0cd825b6b09b5fdb7ad37f8066151ee42d3fc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938093"
---
# <a name="scccloseproject-function"></a>SccCloseProject 函式
此函式會關閉專案時，標示特定的工作階段結束。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
### <a name="parameters"></a>參數  
 pvContext  
 原始檔控制外掛程式的內容結構。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功關閉專案。|  
|SCC_E_PROJNOTOPEN|沒有任何專案目前開啟。|  
|SCC_E_NOTAUTHORIZED|若要執行這項作業不允許的使用者。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗。|  
  
## <a name="remarks"></a>備註  
 [SccOpenProject](../extensibility/sccopenproject-function.md)一定會呼叫此函式前面。 呼叫此函式接下來是呼叫`SccOpenProject`函式或[SccUninitialize](../extensibility/sccuninitialize-function.md)，完全結束原始檔控制系統的連線。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)