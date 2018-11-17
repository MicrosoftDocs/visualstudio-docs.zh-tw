---
title: SccDirDiff 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d2c45773a9d45c69cfed4f773bc5cdfcfa1c305
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791185"
---
# <a name="sccdirdiff-function"></a>SccDirDiff 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此函式會顯示目前的本機目錄上的用戶端磁碟和對應的專案，原始檔控制下的差異。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>參數  
 pContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 hWnd  
 [in]原始檔控制外掛程式時，可以使用當做父代上，它會提供任何對話方塊 IDE 視窗的控制代碼。  
  
 lpDirName  
 [in]要顯示 visual 差異的本機目錄的完整的路徑。  
  
 dwFlags  
 [in]命令旗標 (請參閱 < 備註 > 一節)。  
  
 pvOptions  
 [in]原始檔控制外掛程式特定選項。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|在磁碟上的目錄是在原始程式碼控制專案相同。|  
|SCC_I_FILESDIFFER|在磁碟上的目錄與不同原始程式碼控制中的專案。|  
|SCC_I_RELOADFILE|必須重新載入檔案或專案。|  
|SCC_E_FILENOTCONTROLLED|目錄不是在原始檔控制之下。|  
|SCC_E_NOTAUTHORIZED|若要執行這項作業不允許的使用者。|  
|SCC_E_ACCESSFAILURE|發生問題，存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不明確的失敗。|  
|SCC_E_FILENOTEXIST|找不到本機目錄。|  
  
## <a name="remarks"></a>備註  
 此函式用來指示原始檔控制外掛程式，以便向使用者顯示一份指定的目錄的變更。 外掛程式會自己的視窗中，開啟其選擇，以顯示在磁碟上的使用者的目錄和版本控制下對應的專案之間的差異的格式。  
  
 如果外掛程式支援的比較在所有的目錄，就必須支援比較的目錄，檔案名稱的基礎上即使不支援 「 快速 diff"選項即可。  
  
|`dwFlags`|解譯|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|不區分大小寫的比較 （可能會用來快速的差異或視覺效果）。|  
|SCC_DIFF_IGNORESPACE|會忽略泛空白字元 （可能會用來快速差異或視覺效果）。|  
|SCC_DIFF_QD_CONTENTS|如果支援原始檔控制外掛程式，以無訊息方式比較位元組的目錄。|  
|SCC_DIFF_QD_CHECKSUM|如果外掛程式支援，以無訊息方式比較總和檢查碼，透過目錄，或如果不受支援，會回復到 SCC_DIFF_QD_CONTENTS。|  
|SCC_DIFF_QD_TIME|如果外掛程式支援，以無訊息方式比較時間戳記，透過目錄，或如果不支援，便會回到 SCC_DIFF_QD_CHECKSUM 或 SCC_DIFF_QD_CONTENTS。|  
  
> [!NOTE]
>  此函式會使用相同的命令旗標，作為[SccDiff](../extensibility/sccdiff-function.md)。 不過，原始檔控制外掛程式，可以選擇不支援目錄的 「 快速 diff"作業。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)

