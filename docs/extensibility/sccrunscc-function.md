---
title: SccRunScc 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 40c9ced01c16315840194e770a05ba34df4a9321
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920790"
---
# <a name="sccrunscc-function"></a>SccRunScc 函式
此函式會叫用原始檔控制系統管理工具。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
);  
```  
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 hWnd  
 [in]原始檔控制外掛程式時，可以使用當做父代上，它會提供任何對話方塊 IDE 視窗的控制代碼。  
  
 nFiles  
 [in]中指定的檔案數目`lpFileNames`陣列。  
  
 lpFileNames  
 [in]選取的檔案名稱的陣列。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|原始檔控制系統管理工具已成功叫用。|  
|SCC_I_OPERATIONCANCELED|作業已取消。|  
|SCC_E_INITIALIZEFAILED|無法初始化原始檔控制系統。|  
|SCC_E_ACCESSFAILURE|發生問題，存取原始檔控制系統，可能是因為網路或競爭問題。|  
|SCC_E_CONNECTIONFAILURE|無法連線至原始檔控制系統。|  
|SCC_E_FILENOTCONTROLLED|選取的檔案不在原始檔控制中。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗。|  
  
## <a name="remarks"></a>備註  
 此函式可讓呼叫者透過外部系統管理工具存取的原始檔控制系統功能的完整範圍。 如果原始檔控制系統不有任何使用者介面，原始檔控制外掛程式可以實作介面以執行必要的管理功能。  
  
 此函式呼叫計數與目前所選檔案的檔案名稱的陣列。 如果系統管理工具支援的檔案清單可出現在管理介面中的檔案否則，您可以忽略清單。  
  
 當使用者選取此函式通常叫用**啟動\<原始檔控制伺服器 >** 從**檔案** -> **原始檔控制**功能表。 這**啟動**可以一律停用或甚至是藉由設定登錄項目隱藏功能表選項。 請參閱[如何： 安裝原始檔控制外掛程式](../extensibility/internals/how-to-install-a-source-control-plug-in.md)如需詳細資訊。 只有當呼叫此函式[SccInitialize](../extensibility/sccinitialize-function.md)會傳回`SCC_CAP_RUNSCC`功能位元 (請參閱[功能旗標](../extensibility/capability-flags.md)如需有關這個和其他功能位元為單位)。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [如何： 安裝原始檔控制外掛程式](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [功能旗標](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)