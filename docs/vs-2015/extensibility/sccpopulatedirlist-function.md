---
title: SccPopulateDirList 函式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6078f0fd90855c432b333fd5967367460d0a364e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200019"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此函式會判斷哪些目錄和 （選擇性） 檔案會儲存在原始檔控制，提供要檢查的目錄清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### <a name="parameters"></a>參數  
 pContext  
 [in]原始檔控制外掛程式的內容指標。  
  
 nDirs  
 [in]中的目錄路徑數目`lpDirPaths`陣列。  
  
 lpDirPaths  
 [in]若要檢查的目錄路徑的陣列。  
  
 pfnPopulate  
 [in]每個目錄路徑和 （選擇性） 中的檔案名稱呼叫的回呼函式`lpDirPaths`(請參閱 < [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)如需詳細資訊)。  
  
 pvCallerData  
 [in]要傳遞的值不變之回呼函式。  
  
 fOptions  
 [in]控制目錄的處理方式的值的組合 (請參閱 「 PopulateDirList 旗標 」 一節[特定的命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)可能的值)。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功完成作業。|  
|SCC_E_UNKNOWNERROR|發生錯誤。|  
  
## <a name="remarks"></a>備註  
 只有這些目錄及 （選擇性） 實際上是在原始檔控制儲存機制的檔案名稱會傳遞至回呼函式中。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [錯誤碼](../extensibility/error-codes.md)
