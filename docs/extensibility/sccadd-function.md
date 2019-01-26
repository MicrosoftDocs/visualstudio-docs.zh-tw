---
title: SccAdd 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5124088599eced9d5ae6bc17365d06dc36f81987
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027889"
---
# <a name="sccadd-function"></a>SccAdd 函式
此函式會將新檔案加入至原始檔控制系統。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccAdd(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG*     pfOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
### <a name="parameters"></a>參數  
 pvContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 hWnd  
 [in]原始檔控制外掛程式時，可以使用當做父代上，它會提供任何對話方塊 IDE 視窗的控制代碼。  
  
 nFiles  
 [in]選取要加入至目前的專案中所指定的檔案數目`lpFileNames`陣列。  
  
 lpFileNames  
 [in]要加入之檔案的完整本機名稱的陣列。  
  
 lpComment  
 [in]要套用到所有要加入的檔案的註解。  
  
 pfOptions  
 [in]命令旗標，提供每個檔案的陣列。  
  
 pvOptions  
 [in]原始檔控制外掛程式特定選項。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|新增作業已成功。|  
|SCC_E_FILEALREADYEXISTS|選取的檔案已在原始檔控制中。|  
|SCC_E_TYPENOTSUPPORTED|（例如，二進位） 檔案的類型不支援的原始檔控制系統。|  
|SCC_E_OPNOTSUPPORTED|原始檔控制系統不支援這項作業。|  
|SCC_E_ACCESSFAILURE|發生問題，存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_NOTAUTHORIZED|若要執行這項作業不允許的使用者。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗;將不會執行。|  
|SCC_I_OPERATIONCANCELED|作業已完成前取消。|  
|SCC_I_RELOADFILE|必須重新載入檔案或專案。|  
|SCC_E_FILENOTEXIST|找不到本機檔案。|  
  
## <a name="remarks"></a>備註  
 一般`fOptions`陣列中，取代以下`pfOptions`，使用其中一個`LONG`選項每個檔案的規格。 這是因為檔案類型可能會不同檔案。  
  
> [!NOTE]
>  是無效的同時指定兩者`SCC_FILETYPE_TEXT`和`SCC_FILETYPE_BINARY`選項相同的檔案，但卻是有效都不指定。 設定都不是設定相同`SCC_FILETYPE_AUTO`，在此情況下的原始檔控制外掛程式會自動偵測 dll 的檔案類型。  
  
 以下是使用中的旗標的清單`pfOptions`陣列：  
  
|選項|值|意義|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0x00|原始檔控制外掛程式應該會偵測檔案類型。|  
|SCC_FILETYPE_TEXT|0x01|表示 ASCII 文字檔。|  
|SCC_FILETYPE_BINARY|0x02|表示非 ASCII 文字檔案類型。|  
|SCC_ADD_STORELATEST|0x04|儲存檔案，也就是沒有差異的最新複本。|  
|SCC_FILETYPE_TEXT_ANSI|0x08|您可以將檔案視為 ANSI 文字。|  
|SCC_FILETYPE_UTF8|0x10|您可以將檔案視為 UTF8 格式的 Unicode 文字。|  
|SCC_FILETYPE_UTF16LE|0x20|將檔案視為 Unicode 文字中 UTF16 Little Endian 格式。|  
|SCC_FILETYPE_UTF16BE|0x40|視為成 UTF16 Big Endian Unicode 文字的檔案格式。|  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)