---
title: "SccWillCreateSccFile 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccWillCreateSccFile"
helpviewer_keywords: 
  - "SccWillCreateSccFile 函式"
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccWillCreateSccFile 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式判斷原始檔控制外掛程式是否支援 MSSCCPRJ 的建立。SCC 檔案，每個指定的檔案。  
  
## 語法  
  
```cpp#  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### 參數  
 pContext  
 \[\] in原始檔控制外掛程式的內容指標。  
  
 nFiles  
 \[\] in檔案名稱中包含的數字 `lpFileNames` 陣列的長度以及 `pbSccFiles` 陣列。  
  
 lpFileNames  
 \[\] in若要檢查的完整的檔案名稱的陣列 \(必須由呼叫端配置陣列\)。  
  
 pbSccFiles  
 \[in、 out\]用來儲存結果的陣列。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|成功。|  
|SCC\_E\_INVALIDFILEPATH|有一個陣列中的路徑不正確。|  
|SCC\_E\_NONSPECIFICERROR|非特定的失敗。|  
  
## 備註  
 若要確認是否原始檔控制外掛程式提供 MSSCCPRJ 中的支援的檔案清單，會呼叫此函數。SCC 檔案，每個指定的檔案 \(如需有關 MSSCCPRJ 的詳細資訊。SCC 檔案，請參閱 [MSSCCPRJ。SCC 檔案](../extensibility/mssccprj-scc-file.md)\)。 原始檔控制外掛程式可以宣告它們是否具有建立 MSSCCPRJ 的功能。SCC 檔案，藉由宣告 `SCC_CAP_SCCFILE` 在初始化期間。 此外掛程式會傳回 `TRUE` 或 `FALSE` 每個檔案中 `pbSccFiles` 陣列，表示其中一個指定的檔案有 MSSCCPRJ。SCC 的支援。 如果外掛程式傳回成功的程式碼從函式，傳回陣列中的值都會被接受。 在失敗時，陣列會被忽略。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [MSSCCPRJ。SCC 檔案](../extensibility/mssccprj-scc-file.md)