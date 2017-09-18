---
title: "SccDiff 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccDiff"
helpviewer_keywords: 
  - "SccDiff 函式"
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# SccDiff 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會顯示 \(或選擇性地只會檢查\) 目前的檔案 \(位於本機磁碟上\) 和最後一個簽入的版本之間差異，在來源控制系統。  
  
## 語法  
  
```cpp#  
SCCRTN SccDiff(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LPCSTR    lpFileName,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### 參數  
 pvContext  
 \[\] in原始檔控制外掛程式內容結構。  
  
 hWnd  
 \[\] in原始檔控制外掛程式可以使用為父代，它會提供任何對話方塊 IDE 視窗控制代碼。  
  
 lpFileName  
 \[\] in要求不同的檔案名稱。  
  
 Stored  
 \[\] in命令旗標。 如需詳細資訊，請參閱 \< 備註 \>。  
  
 pvOptions  
 \[\] in原始檔控制外掛程式專屬選項。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|工作複本與伺服器版本都相同。|  
|SCC\_I\_FILESDIFFERS|工作複本與原始檔控制下的版本不同。|  
|SCC\_I\_RELOADFILE|需要重新載入檔案或專案。|  
|SCC\_E\_FILENOTCONTROLLED|檔案不是原始檔控制下。|  
|SCC\_E\_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC\_E\_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC\_E\_NONSPECIFICERROR|非特定的失敗。未取得檔案的差異。|  
|SCC\_E\_FILENOTEXIST|找不到本機檔案。|  
  
## 備註  
 此函式有兩種不同的用途。 根據預設，它顯示檔案的變更清單。 原始檔控制外掛程式開啟它自己的視窗中選擇，以顯示磁碟上的使用者的檔案與原始檔控制下之檔案的最新版本之間的差異的格式。  
  
 或者，IDE 可能只需要判斷檔案是否已變更。 例如，IDE 可能需要以判斷它是否能安全簽出檔案，而不通知使用者。 在此情況下，IDE 會傳入 `SCC_DIFF_CONTENTS` 旗標。 原始檔控制外掛程式必須檢查磁碟，位元組的對原始檔控制的檔案上的檔案，並傳回值，指出兩個檔案而不會向使用者顯示任何項目是否不同。  
  
 一種效能最佳化，原始檔控制外掛程式可能會使用總和檢查碼或時間戳記，而不需要針對呼叫的位元組的比較為基礎的替代項目 `SCC_DIFF_CONTENTS`: 這些形式的比較會很明顯地更快，但較不可靠。 並非所有的原始檔控制系統可能會支援這些替代的比較方法，以及外掛程式可能需要切換回內容比較。 所有的原始檔控制外掛程式時，至少必須支援內容比較。  
  
> [!NOTE]
>  快速差異旗標互斥。 有效傳遞任何旗標，但同時傳遞多個無效。`SCC_DIFF_QUICK_DIFF`, 這結合了所有的旗標的遮罩可以用來測試，但它應該永遠不會做為參數傳遞。  
  
|`fOption`|意義|  
|---------------|--------|  
|SCC\_DIFF\_IGNORECASE|不區分大小寫的比較 \(可能用來快速或視覺化差異\)。|  
|SCC\_DIFF\_IGNORESPACE|會忽略泛空白字元 \(可能用來快速或視覺化差異\)。|  
|SCC\_DIFF\_QD\_CONTENTS|以無訊息模式比較位元組的檔案。|  
|SCC\_DIFF\_QD\_CHECKSUM|以無訊息模式會比較總和檢查碼時支援透過檔案。 如果不支援，回復到內容的比較。|  
|SCC\_DIFF\_QD\_TIME|以無訊息模式比較透過支援時，其時間戳記的檔案。 如果不支援，回復到內容的比較。|  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)