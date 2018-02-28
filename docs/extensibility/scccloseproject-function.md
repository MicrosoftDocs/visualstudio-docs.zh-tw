---
title: "SccCloseProject 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 70b0e693f4223c9fe004170a0ed1b4b70c6de442
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="scccloseproject-function"></a>SccCloseProject 函式
此函式會關閉專案時，結尾的特定工作階段。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>參數  
 pvContext  
 原始檔控制外掛程式的內容結構。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功關閉專案。|  
|SCC_E_PROJNOTOPEN|沒有任何專案目前開啟。|  
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗。|  
  
## <a name="remarks"></a>備註  
 [SccOpenProject](../extensibility/sccopenproject-function.md)一律會呼叫此函式之前。 此函式的呼叫之後接著呼叫`SccOpenProject`函式或[SccUninitialize](../extensibility/sccuninitialize-function.md)，這完全結束原始檔控制系統的連線。  
  
## <a name="see-also"></a>請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)