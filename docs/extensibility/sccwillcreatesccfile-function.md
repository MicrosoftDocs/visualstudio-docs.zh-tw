---
title: SccWillCreateSccFile 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af6da09badf0ffea4846d35fe00b4ca146243d64
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile 函式
此函式判斷原始檔控制外掛程式是否支援 MSSCCPRJ 的建立。SCC 檔案，每個指定的檔案。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### <a name="parameters"></a>參數  
 pContext  
 [in]原始檔控制外掛程式的內容指標。  
  
 nFiles  
 [in]檔案名稱中包含的數字`lpFileNames`陣列的長度以及`pbSccFiles`陣列。  
  
 lpFileNames  
 [in]若要檢查完整的檔案名稱的陣列 （必須由呼叫端配置陣列）。  
  
 pbSccFiles  
 [in、 out]用來儲存結果的陣列。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|成功。|  
|SCC_E_INVALIDFILEPATH|其中一個陣列中的路徑無效。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗。|  
  
## <a name="remarks"></a>備註  
 一份檔案，以決定是否原始檔控制外掛程式在提供支援 MSSCCPRJ 呼叫此函式。SCC 檔案，每個指定的檔案 （如需有關 MSSCCPRJ 的詳細資訊。SCC 檔案，請參閱[MSSCCPRJ。SCC 檔案](../extensibility/mssccprj-scc-file.md))。 原始檔控制外掛程式可以宣告它們是否具備建立 MSSCCPRJ 的功能。SCC 檔案，藉由宣告`SCC_CAP_SCCFILE`初始化期間。 外掛程式傳回`TRUE`或`FALSE`為每個檔案`pbSccFiles`陣列來指出指定的檔案必須有 MSSCCPRJ。SCC 支援。 如果外掛程式從函式傳回成功碼，傳回陣列中的值都會被接受。 如果失敗，陣列會被忽略。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [MSSCCPRJ.SCC 檔案](../extensibility/mssccprj-scc-file.md)