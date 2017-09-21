---
title: "SccGet 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGet"
helpviewer_keywords: 
  - "SccGet 函式"
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccGet 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會擷取一或多個檔案，來檢視及編譯，而不是用於編輯的複本。 在大多數的系統檔案被標記為唯讀。  
  
## 語法  
  
```cpp#  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### 參數  
 pvContext  
 \[\] in原始檔控制外掛程式內容結構。  
  
 hWnd  
 \[\] in原始檔控制外掛程式可以使用為父代，它會提供任何對話方塊 IDE 視窗控制代碼。  
  
 nFiles  
 \[\] in中指定的檔案數目 `lpFileNames` 陣列。  
  
 lpFileNames  
 \[\] in要擷取檔案的完整名稱的陣列。  
  
 Stored  
 \[\] in命令旗標 \(`SCC_GET_ALL`, ，`SCC_GET_RECURSIVE`\)。  
  
 pvOptions  
 \[\] in原始檔控制外掛程式專屬選項。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|取得作業成功。|  
|SCC\_E\_FILENOTCONTROLLED|檔案不是原始檔控制下。|  
|SCC\_E\_OPNOTSUPPORTED|原始檔控制系統不支援這項作業。|  
|SCC\_E\_FILEISCHECKEDOUT|無法取得目前使用者已簽出檔案。|  
|SCC\_E\_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC\_E\_NOSPECIFIEDVERSION|指定無效的版本或日期\/時間。|  
|SCC\_E\_NONSPECIFICERROR|非特定的失敗。檔案並未同步處理。|  
|SCC\_I\_OPERATIONCANCELED|在完成之前取消作業。|  
|SCC\_E\_NOTAUTHORIZED|使用者沒有執行這項作業的權限。|  
  
## 備註  
 以計數和要擷取的檔案名稱的陣列，會呼叫此函數。 如果在 IDE 通過旗標 `SCC_GET_ALL`, ，這表示中的項目 `lpFileNames` 不是檔案，而目錄，並在指定的目錄中的原始檔控制下的所有檔案都都要擷取。  
  
 `SCC_GET_ALL` 旗標可以結合 `SCC_GET_RECURSIVE` 旗標來擷取指定的目錄中的所有檔案和所有的子目錄。  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE` 永遠不會傳遞而不 `SCC_GET_ALL`。 另外請注意，是否同時傳遞遞迴取得目錄 C:\\A 和 C:\\A\\B，C:\\A\\B 及其所有子目錄會實際擷取兩次。 是 IDE 的責任，並不是原始檔控制外掛程式，藉此確定這類的重複項目會保留超出陣列。  
  
 最後，即使原始檔控制外掛程式指定 `SCC_CAP_GET_NOUI` 上初始化時，指出它並沒有 Get 命令的使用者介面，來擷取檔案 IDE 仍可能會呼叫此函式的旗標。 旗標只是表示，IDE 不會顯示一個 Get 功能表項目，外掛程式不需要提供任何 UI。  
  
## 重新命名和 SccGet  
 情況: 使用者簽出檔案，例如 a.txt 並加以修改。 A.txt 可以簽入之前，第二個使用者重新命名為 b.txt 原始檔控制資料庫中的 a.txt、 簽出 b.txt，便會進行一些修改檔案，和簽入檔案。 第一位使用者想要讓第一位使用者將自己的本機版本的 a.txt 檔案重新命名為 b.txt 並沒有取得新的檔案，第二個使用者所做的變更。 不過，本機快取，可追蹤的版本號碼仍然認為 a.txt 的第一個版本儲存在本機，因此原始檔控制無法解析的差異。  
  
 有兩種方式可以解決這種情況下，本機快取的原始檔控制版本會與原始檔控制資料庫同步處理變成:  
  
1.  不允許重新命名目前已簽出原始檔控制資料庫中的檔案。  
  
2.  執行 「 刪除舊 」 後面接著 「 新增 」 的對應項。 下列演算法是一種方式完成這項作業。  
  
    1.  呼叫 [SccQueryChanges](../extensibility/sccquerychanges-function.md) 來了解重新命名為 b.txt 原始檔控制資料庫中的 a.txt 函式。  
  
    2.  將本機 a.txt 重新命名為 b.txt。  
  
    3.  呼叫 `SccGet` a.txt 和 b.txt 函式。  
  
    4.  因為 a.txt 不存在於原始檔控制資料庫中，本機版本快取清除遺漏的 a.txt 版本資訊。  
  
    5.  B.txt 檔案簽出本機 b.txt 檔案的內容會合併。  
  
    6.  現在可以更新的 b.txt 檔案簽入。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)