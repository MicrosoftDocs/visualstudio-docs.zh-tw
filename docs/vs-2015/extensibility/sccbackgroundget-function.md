---
title: SccBackgroundGet 函式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 118d8458fd9581a87baea08452d0011d4d66c9a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838901"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此函式會從原始檔控制每個指定的檔案，而不是使用者互動。  
  
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
 在原始檔控制外掛程式內容指標。  
  
 nFiles  
 在陣列中指定的檔案數目 `lpFileNames` 。  
  
 lpFileNames  
 [in，out]要抓取之檔案的名稱陣列。  
  
> [!NOTE]
> 這些名稱必須是完整的本機檔案名。  
  
 dwFlags  
 在命令旗標 (`SCC_GET_ALL` ， `SCC_GET_RECURSIVE`) 。  
  
 dwBackgroundOperationID  
 在與此作業相關聯的唯一值。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|作業順利完成。|  
|SCC_E_BACKGROUNDGETINPROGRESS|背景抓取已經在進行中 (當原始檔控制外掛程式不支援) 的並行批次作業時，才應該傳回此功能。|  
|SCC_I_OPERATIONCANCELED|作業已在完成前取消。|  
  
## <a name="remarks"></a>備註  
 這個函式一律會在與載入原始檔控制外掛程式不同的執行緒上呼叫。 在完成之前，不應傳回此函式。不過，您可以使用多個檔案清單多次呼叫它，而這兩者都是在同一時間進行。  
  
 使用 `dwFlags` 引數與 [SccGet](../extensibility/sccget-function.md)相同。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)
