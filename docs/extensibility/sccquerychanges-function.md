---
title: SccQueryChanges 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f7b3a9454daa0f2e3c5cf91a9dc483afe1f635a1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915707"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges 函式
此函式會列舉指定的檔案，提供透過回呼函式的每個檔案的名稱變更的相關資訊清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### <a name="parameters"></a>參數  
 pContext  
 [in]原始檔控制外掛程式的內容指標。  
  
 nFiles  
 [in]中的檔案數目`lpFileNames`陣列。  
  
 lpFileNames  
 [in]若要取得相關資訊的檔案名稱的陣列。  
  
 pfnCallback  
 [in]若要在清單中的每個檔案名稱呼叫的回呼函式 (請參閱[QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)如需詳細資訊)。  
  
 pvCallerData  
 [in]將會原封不動地傳遞至回呼函式的值。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|查詢處理序已順利完成。|  
|SCC_E_PROJNOTOPEN|不在原始檔控制開啟專案。|  
|SCC_E_ACCESSFAILURE|發生問題，存取原始檔控制系統，可能是因為網路或競爭問題。|  
|SCC_E_NONSPECIFICERROR|發生未指定或一般錯誤。|  
  
## <a name="remarks"></a>備註  
 要查詢的變更會為命名空間： 具體而言，重新命名、 新增和移除檔案。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [錯誤碼](../extensibility/error-codes.md)