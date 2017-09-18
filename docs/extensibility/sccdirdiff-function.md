---
title: "SccDirDiff 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccDirDiff"
helpviewer_keywords: 
  - "SccDirDiff 函式"
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# SccDirDiff 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會顯示目前的本機目錄上的用戶端磁碟和原始檔控制下對應的專案之間的差異。  
  
## 語法  
  
```cpp#  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### 參數  
 pContext  
 \[\] in原始檔控制外掛程式內容結構。  
  
 hWnd  
 \[\] in原始檔控制外掛程式可以使用為父代，它會提供任何對話方塊 IDE 視窗控制代碼。  
  
 lpDirName  
 \[\] in要為其顯示視覺化差異的本機目錄的完整的路徑。  
  
 dwFlags  
 \[\] in命令旗標 \(請參閱 \< 備註 \> 一節\)。  
  
 pvOptions  
 \[\] in原始檔控制外掛程式專屬選項。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|在磁碟上的目錄是在原始程式碼控制的專案相同。|  
|SCC\_I\_FILESDIFFER|在磁碟上的目錄與原始程式碼控制中的專案不同。|  
|SCC\_I\_RELOADFILE|需要重新載入檔案或專案。|  
|SCC\_E\_FILENOTCONTROLLED|目錄不是原始程式碼控制之下。|  
|SCC\_E\_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC\_E\_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|非特定的失敗。|  
|SCC\_E\_FILENOTEXIST|找不到本機目錄。|  
  
## 備註  
 此函式用來指示的原始檔控制外掛程式，以顯示給使用者的變更至指定的目錄清單。 外掛程式就會開啟它自己的視窗中，選擇，以顯示磁碟上的使用者的目錄和版本控制下對應的專案之間差異的格式。  
  
 如果外掛程式支援的比較所有的目錄，它必須支援目錄的比較，以檔案名稱為基礎即使不支援 「 快速差異 」 選項即可。  
  
|`dwFlags`|解譯|  
|---------------|--------|  
|SCC\_DIFF\_IGNORECASE|\(可用於快速差異或視覺\) 不區分大小寫的比較。|  
|SCC\_DIFF\_IGNORESPACE|會忽略泛空白字元 \(可能用來快速差異或視覺\)。|  
|SCC\_DIFF\_QD\_CONTENTS|如果原始檔控制外掛程式支援，以無訊息模式比較位元組的目錄。|  
|SCC\_DIFF\_QD\_CHECKSUM|如果外掛程式支援，以無訊息模式會比較總和檢查碼，透過目錄，或如果不支援，就會回到 SCC\_DIFF\_QD\_CONTENTS。|  
|SCC\_DIFF\_QD\_TIME|如果外掛程式支援，以無訊息模式會比較時間戳記，透過目錄，或如果不支援，便會回到 SCC\_DIFF\_QD\_CHECKSUM 或 SCC\_DIFF\_QD\_CONTENTS。|  
  
> [!NOTE]
>  此函式會使用相同的命令旗標為 [SccDiff](../extensibility/sccdiff-function.md)。 不過，可以選擇原始檔控制外掛程式不支援目錄的 「 快速差異 」 作業。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)