---
title: "SccAdd 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccAdd"
helpviewer_keywords: 
  - "SccAdd 函式"
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# SccAdd 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會將新檔案加入至原始檔控制系統。  
  
## 語法  
  
```cpp#  
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
  
#### 參數  
 pvContext  
 \[\] in原始檔控制外掛程式內容結構。  
  
 hWnd  
 \[\] in原始檔控制外掛程式可以使用為父代，它會提供任何對話方塊 IDE 視窗控制代碼。  
  
 nFiles  
 \[\] in選取要新增至目前專案中所指定的檔案數目 `lpFileNames` 陣列。  
  
 lpFileNames  
 \[\] in要加入的檔案的完整限定本機名稱的陣列。  
  
 lpComment  
 \[\] in要套用到所有的檔案加入註解。  
  
 pfOptions  
 \[\] in命令旗標，提供每個檔案為基礎的陣列。  
  
 pvOptions  
 \[\] in原始檔控制外掛程式專屬選項。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|加入作業成功。|  
|SCC\_E\_FILEALREADYEXISTS|選取的檔案已經在原始檔控制中。|  
|SCC\_E\_TYPENOTSUPPORTED|\(例如，二進位\) 檔案的類型不受到原始檔控制系統。|  
|SCC\_E\_OPNOTSUPPORTED|原始檔控制系統不支援這項作業。|  
|SCC\_E\_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC\_E\_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC\_E\_NONSPECIFICERROR|非特定的失敗。將不會執行。|  
|SCC\_I\_OPERATIONCANCELED|在完成之前已取消作業。|  
|SCC\_I\_RELOADFILE|需要重新載入檔案或專案。|  
|SCC\_E\_FILENOTEXIST|找不到本機檔案。|  
  
## 備註  
 一般 `fOptions` 陣列，來取代以下 `pfOptions`, ，其中一個 `LONG` 選項每個檔案規格。 這是因為檔案類型而異檔案。  
  
> [!NOTE]
>  不能同時指定 `SCC_FILETYPE_TEXT` 和 `SCC_FILETYPE_BINARY` 選項相同的檔案，但卻是適用於指定兩者。 設定都不是設定相同 `SCC_FILETYPE_AUTO`, ，在此情況下的原始檔控制外掛程式 autodetects 檔案類型。  
  
 以下是使用的旗標的清單 `pfOptions` 陣列:  
  
|選項|值|意義|  
|--------|-------|--------|  
|SCC\_FILETYPE\_AUTO|0x00|原始檔控制外掛程式應該會偵測到的檔案類型。|  
|SCC\_FILETYPE\_TEXT|0x01|表示一個 ASCII 文字檔。|  
|SCC\_FILETYPE\_BINARY|0x02|指出 ASCII 文字以外的檔案類型。|  
|SCC\_ADD\_STORELATEST|0x04|儲存檔案，沒有差異的最新複本。|  
|SCC\_FILETYPE\_TEXT\_ANSI|0x08|您可以將檔案視為 ANSI 文字。|  
|SCC\_FILETYPE\_UTF8|0x10|將檔案視為 Unicode UTF8 格式的文字。|  
|SCC\_FILETYPE\_UTF16LE|0x20|將檔案視為 Unicode 文字 UTF16 Little Endian 格式。|  
|SCC\_FILETYPE\_UTF16BE|0x40|視為成 UTF16 Big Endian Unicode 文字檔案格式。|  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)