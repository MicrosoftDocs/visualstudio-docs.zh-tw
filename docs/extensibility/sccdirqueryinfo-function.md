---
title: SccDirQueryInfo 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1de32b8502e40c953bd7080d64e56047e6bb5ce9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140364"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo 函式
此函式會檢查完整的目錄清單及其目前狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>參數  
 pContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 nDirs  
 [in]選取要查詢的目錄數目。  
  
 lpDirNames  
 [in]要查詢目錄的完整路徑的陣列。  
  
 lpStatus  
 [in、 out]原始檔控制外掛程式傳回的狀態旗標的陣列結構 (請參閱[目錄狀態碼](../extensibility/directory-status-code-enumerator.md)如需詳細資訊)。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|查詢已成功。|  
|SCC_E_OPNOTSUPPORTED|原始程式碼控制系統不支援這項作業。|  
|SCC_E_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不明確的失敗。|  
  
## <a name="remarks"></a>備註  
 函式會傳回陣列所使用的位元的位元遮罩填滿`SCC_DIRSTATUS`系列 (請參閱[目錄狀態碼](../extensibility/directory-status-code-enumerator.md))，每個目錄指定一個項目。 狀態陣列是由呼叫端所配置的。  
  
 若要檢查目錄是否在原始檔控制中，藉由查詢是否有對應的專案重新命名目錄之前，IDE 會使用此函式。 如果目錄不是原始檔控制下，IDE 可以提供適當的警告給使用者。  
  
> [!NOTE]
>  如果原始檔控制外掛程式選擇實作一個或多個狀態的值，未實作的 bits 應該設定為零。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [目錄的狀態碼](../extensibility/directory-status-code-enumerator.md)