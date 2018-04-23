---
title: SccAdd 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2933d00b7450f946a5fd5409bcaeecc2527a9f64
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
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
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 hWnd  
 [in]原始檔控制外掛程式之任何它所提供的對話方塊，可以使用為父代 IDE 視窗的控制代碼。  
  
 nFiles  
 [in]選取要新增至目前的專案中所指定的檔案數目`lpFileNames`陣列。  
  
 lpFileNames  
 [in]要新增檔案的完整限定本機名稱的陣列。  
  
 lpComment  
 [in]要套用至所有加入的檔案的註解。  
  
 pfOptions  
 [in]命令旗標，每個檔案所提供的陣列。  
  
 pvOptions  
 [in]原始檔控制外掛程式特定選項。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|加入作業成功。|  
|SCC_E_FILEALREADYEXISTS|選取的檔案已經在原始檔控制中。|  
|SCC_E_TYPENOTSUPPORTED|（例如，二進位） 檔案的類型不受原始檔控制系統。|  
|SCC_E_OPNOTSUPPORTED|原始檔控制系統不支援這項作業。|  
|SCC_E_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗。將不會執行。|  
|SCC_I_OPERATIONCANCELED|作業已完成前取消。|  
|SCC_I_RELOADFILE|需要重新載入檔案或專案。|  
|SCC_E_FILENOTEXIST|找不到本機檔案。|  
  
## <a name="remarks"></a>備註  
 一般`fOptions`陣列，來取代這裡`pfOptions`，其中包含一個`LONG`選項每個檔案的規格。 這是因為檔案類型而異檔案至檔案。  
  
> [!NOTE]
>  是無效的同時指定`SCC_FILETYPE_TEXT`和`SCC_FILETYPE_BINARY`選項相同的檔案，但卻是適用於指定兩者。 設定都不是設定相同`SCC_FILETYPE_AUTO`，在此情況下的原始檔控制外掛程式 autodetects 檔案類型。  
  
 以下是使用中的旗標的清單`pfOptions`陣列：  
  
|選項|值|意義|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0x00|原始檔控制外掛程式應該會偵測到的檔案類型。|  
|SCC_FILETYPE_TEXT|0x01|表示 ASCII 文字檔案。|  
|SCC_FILETYPE_BINARY|0x02|表示非 ASCII 文字檔案類型。|  
|SCC_ADD_STORELATEST|0x04|儲存檔案，沒有差異的最新複本。|  
|SCC_FILETYPE_TEXT_ANSI|0x08|您可以將檔案視為 ANSI 文字。|  
|SCC_FILETYPE_UTF8|0x10|視為 UTF8 格式的 Unicode 文字檔案。|  
|SCC_FILETYPE_UTF16LE|0x20|將檔案視為 Unicode 文字中 UTF16 Little Endian 格式。|  
|SCC_FILETYPE_UTF16BE|0x40|將檔案以在 UTF16 Big Endian Unicode 文字格式化。|  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)