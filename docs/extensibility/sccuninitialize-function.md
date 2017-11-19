---
title: "SccUninitialize 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccUninitialize
helpviewer_keywords: SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 434987489feccd5f576e04d69afbb4b39e1dc754
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="sccuninitialize-function"></a>SccUninitialize 函式
此函式會清除任何配置或由先前呼叫所建立的開啟連接[SccInitialize](../extensibility/sccinitialize-function.md)準備關閉原始檔控制外掛程式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]在中建立的原始檔控制外掛程式的內容結構的指標[SccInitialize](../extensibility/sccinitialize-function.md)。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|說明|  
|-----------|-----------------|  
|SCC_OK|清除工作順利完成。|  
  
## <a name="remarks"></a>備註  
 原始檔控制外掛程式負責準備要關閉並釋放外掛程式有已配置的內容結構的記憶體。 每個外掛程式的特定執行個體一次呼叫函式。 呼叫[SccInitialize](../extensibility/sccinitialize-function.md)位於此呼叫。 任何專案仍然可以開啟時呼叫的`SccUninitialize`。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)