---
title: "SccBackgroundGet 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccBackgroundGet
helpviewer_keywords: SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b63a7e8c9a6b2a4f2539cd6a8426ba9df365ab76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet 函式
此函式會擷取從原始檔控制每個指定的檔案而不需要使用者互動。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccBackgroundGet(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LONG    dwFlags,  
   LONG    dwBackgroundOperationID  
);  
```  
  
#### <a name="parameters"></a>參數  
 pContext  
 [in]原始檔控制外掛程式的內容指標。  
  
 nFiles  
 [in]中指定的檔案數目`lpFileNames`陣列。  
  
 lpFileNames  
 [in、 out]要擷取的檔案名稱的陣列。  
  
> [!NOTE]
>  名稱必須是完整的本機檔案名稱。  
  
 將 dwFlags  
 [in]命令旗標 (`SCC_GET_ALL`， `SCC_GET_RECURSIVE`)。  
  
 dwBackgroundOperationID  
 [in]這項作業相關聯的唯一值。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|作業已順利完成。|  
|SCC_E_BACKGROUNDGETINPROGRESS|背景擷取 」 正在執行 （原始檔控制外掛程式應該傳回這只有在不支援同時批次作業）。|  
|SCC_I_OPERATIONCANCELED|在完成前已取消作業。|  
  
## <a name="remarks"></a>備註  
 此函式一律會在不同於載入原始檔控制外掛程式的一個執行緒上呼叫。 此函式不應該傳回直到完成。不過，它可以與多個清單的檔案，並在相同的時間都呼叫多次。  
  
 使用`dwFlags`引數是相同[SccGet](../extensibility/sccget-function.md)。  
  
## <a name="see-also"></a>請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)