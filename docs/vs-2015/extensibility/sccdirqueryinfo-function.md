---
title: SccDirQueryInfo 函式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7334ddd1ce6c7f9feac63253246e55b65121e18b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432444"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此函式會檢查完整的目錄清單及其目前狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 [in]查詢目錄的完整路徑的陣列。  
  
 lpStatus  
 [in、 out]原始檔控制外掛程式傳回的狀態旗標的陣列結構 (請參閱[目錄狀態碼](../extensibility/directory-status-code-enumerator.md)如需詳細資訊)。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|查詢成功。|  
|SCC_E_OPNOTSUPPORTED|原始程式碼控制系統不支援這項作業。|  
|SCC_E_ACCESSFAILURE|發生問題，存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不明確的失敗。|  
  
## <a name="remarks"></a>備註  
 函式會傳回陣列所使用的位元遮罩的位元的填滿`SCC_DIRSTATUS`系列 (請參閱 <<c2> [ 目錄狀態碼](../extensibility/directory-status-code-enumerator.md))，指定每個目錄的一個項目。 呼叫端配置狀態陣列。  
  
 目錄已重新命名為檢查目錄是否在原始檔控制中，藉由查詢是否有對應的專案之前，IDE 會使用此函式。 如果目錄不是原始檔控制之下，IDE 可以提供適當的警告給使用者。  
  
> [!NOTE]
> 如果原始檔控制外掛程式選擇實作一個或多個狀態的值，未實作的 bits 應該設定為零。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [目錄狀態碼](../extensibility/directory-status-code-enumerator.md)
