---
title: SccHistory 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 464c71d7caeca1b9b8c4c3455dad1737649f5ea4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138196"
---
# <a name="scchistory-function"></a>SccHistory 函式
此函式會顯示指定的檔案歷程記錄。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccHistory(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pvContext`  
 [in]原始檔控制外掛程式的內容結構。  
  
 `hWnd`  
 [in]原始檔控制外掛程式之任何它所提供的對話方塊，可以使用為父代 IDE 視窗的控制代碼。  
  
 `nFiles`  
 [in]中指定的檔案數目`lpFileName`陣列。  
  
 `lpFileName`  
 [in]檔案的完整名稱的陣列。  
  
 `fOptions`  
 [in]（目前未使用） 的命令旗標。  
  
 `pvOptions`  
 [in]原始檔控制外掛程式特定選項。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功取得版本歷程記錄。|  
|SCC_I_RELOADFILE|原始檔控制系統實際修改磁碟上的檔案 （比方說，藉由取得它的舊版本），擷取記錄時，IDE 應重新載入這個檔案。|  
|SCC_E_FILENOTCONTROLLED|檔案不在原始檔控制中。|  
|SCC_E_OPNOTSUPPORTED|原始檔控制系統不支援這項作業。|  
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC_E_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_PROJNOTOPEN|專案是已開啟。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗。 無法取得檔案歷程記錄。|  
  
## <a name="remarks"></a>備註  
 原始檔控制外掛程式可顯示它自己的對話方塊，以顯示每個檔案的歷程記錄使用`hWnd`與父視窗。 或者，選擇性的文字輸出回呼函式提供給[SccOpenProject](../extensibility/sccopenproject-function.md)可以使用，如果受支援。  
  
 請注意，在某些情況下，這個呼叫的執行期間可能會變更所檢查的檔案。 例如，[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]記錄命令可讓使用者有機會取得較舊版本的檔案。 在這種情況下，原始檔控制外掛程式傳回`SCC_I_RELOAD`警告 IDE，需要重新載入檔案。  
  
> [!NOTE]
>  如果原始檔控制外掛程式不支援此函式的檔案陣列，可以顯示只有第一個檔案的檔案歷程記錄。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)