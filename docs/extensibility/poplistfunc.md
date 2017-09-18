---
title: "POPLISTFUNC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "POPDIRLISTFUNC"
helpviewer_keywords: 
  - "POPLISTFUNC 回呼函式"
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# POPLISTFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此回呼會提供給 [SccPopulateList](../extensibility/sccpopulatelist-function.md) ide 而且由原始檔控制外掛程式用來更新檔案或目錄的清單 \(也提供給 `SccPopulateList` 函式\)。  
  
 當使用者選擇 **取得** 命令在 IDE 中，IDE 會顯示使用者可以取得的所有檔案的清單方塊。 不幸的是，IDE 不知道確切的使用者可能會收到; 的所有檔案清單只有外掛程式都具有這份清單。 如果其他使用者將檔案新增至原始檔控制專案中，這些檔案應該會出現在清單中，但 IDE 不知道它們。 IDE 會建置認定可以取得使用者的檔案清單。 向使用者顯示此清單之前，它會呼叫 [SccPopulateList](../extensibility/sccpopulatelist-function.md)`,` 提供原始檔控制外掛程式有機會新增和刪除清單中的檔案。  
  
## 簽章  
 原始檔控制外掛程式會呼叫 IDE 實作函式使用下列的原型，以修改清單:  
  
```cpp#  
typedef BOOL (*POPLISTFUNC) ( LPVOID pvCallerData, BOOL fAddRemove, LONG nStatus, LPSTR lpFileName );  
```  
  
## 參數  
 pvCallerData  
 `pvCallerData` 參數傳遞至呼叫端 \(IDE\) [SccPopulateList](../extensibility/sccpopulatelist-function.md)。 原始檔控制外掛程式應該假設任何有關此參數的內容。  
  
 fAddRemove  
 如果 `TRUE`, ，`lpFileName` 是應加入的檔案清單的檔案。 如果 `FALSE`, ，`lpFileName` 是應該從檔案清單中刪除的檔案。  
  
 nStatus  
 狀態 `lpFileName` \(結合 `SCC_STATUS` 位元; 請參閱 [檔案狀態碼](../extensibility/file-status-code-enumerator.md) 如需詳細資訊\)。  
  
 lpFileName  
 要加入或從清單中刪除的檔案名稱的完整目錄路徑。  
  
## 傳回值  
  
|值|描述|  
|-------|--------|  
|`TRUE`|外掛程式可以繼續呼叫此函式。|  
|`FALSE`|在 IDE 端 \(例如記憶體狀況現成\) 已有問題。 外掛程式應該停止作業。|  
  
## 備註  
 它會針對每個原始檔控制外掛程式想要新增或刪除的檔案清單的檔案，呼叫此函式，並傳入 `lpFileName`。`fAddRemove` 旗標指出新的檔案新增至清單或刪除舊的檔案。`nStatus` 參數指定檔案的狀態。 當外掛程式 SCC 完成加入和刪除檔案時，它會傳回 [SccPopulateList](../extensibility/sccpopulatelist-function.md) 呼叫。  
  
> [!NOTE]
>  `SCC_CAP_POPULATELIST` 功能位元是需要 Visual Studio。  
  
## 請參閱  
 [IDE 所實作的回呼函式](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [檔案狀態碼](../extensibility/file-status-code-enumerator.md)