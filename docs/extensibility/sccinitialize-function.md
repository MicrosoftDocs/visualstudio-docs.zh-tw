---
title: "SccInitialize 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccInitialize
helpviewer_keywords: SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9e688d30d2367236cfcf5b2d14b36eb602832fc0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="sccinitialize-function"></a>SccInitialize 函式
此函式初始化原始檔控制外掛程式，並提供整合式的開發環境 (IDE) 的限制及功能。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccInitialize (  
   LPVOID* ppvContext,  
   HWND    hWnd,  
   LPCSTR  lpCallerName,  
   LPSTR   lpSccName,  
   LPLONG  lpSccCaps,  
   LPSTR   lpAuxPathLabel,  
   LPLONG  pnCheckoutCommentLen,  
   LPLONG  pnCommentLen  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppvContext`  
 [in]原始檔控制外掛程式可以在這裡放其內容結構的指標。  
  
 `hWnd`  
 [in]原始檔控制外掛程式之任何它所提供的對話方塊，可以使用為父代 IDE 視窗的控制代碼。  
  
 `lpCallerName`  
 [in]程式呼叫的原始檔控制外掛程式的名稱。  
  
 `lpSccName`  
 [in、 out]緩衝區的原始檔控制外掛程式，將自己的名稱 (不到超過`SCC_NAME_LEN`)。  
  
 `lpSccCaps`  
 [out]傳回的原始檔控制外掛程式功能旗標。  
  
 `lpAuxPathLabel`  
 [in、 out]原始檔控制外掛程式，將描述的字串緩衝區`lpAuxProjPath`所傳回的參數[SccOpenProject](../extensibility/sccopenproject-function.md)和[SccGetProjPath](../extensibility/sccgetprojpath-function.md) (不到超過`SCC_AUXLABEL_LEN`)。  
  
 `pnCheckoutCommentLen`  
 [out]傳回簽出註解的最大允許長度。  
  
 `pnCommentLen`  
 [out]傳回其他註解的最大允許長度。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|說明|  
|-----------|-----------------|  
|SCC_OK|原始檔控制初始化成功。|  
|SCC_E_INITIALIZEFAILED|系統無法初始化。|  
|SCC_E_NOTAUTHORIZED|不允許使用者執行指定的作業。|  
|SCC_E_NONSPECFICERROR|不明確的失敗。未初始化原始檔控制系統。|  
  
## <a name="remarks"></a>備註  
 在第一次載入原始檔控制外掛程式時，IDE 會呼叫此函式。 它可讓 IDE 來傳遞特定資訊，例如，呼叫端的名稱、 的外掛程式。 IDE 也會取得回特定資訊，例如註解和功能的隨插即用單元的最大容許長度。  
  
 `ppvContext`指向`NULL`指標。 原始檔控制外掛程式可以配置供其使用的結構，並儲存在該結構的指標`ppvContext`。 IDE 會將這個指標傳遞至每個其他 VSSCI API 函式允許外掛程式有可用的內容資訊，而不必全域儲存體，並支援多個外掛程式執行個體。 此結構應該取消配置時[SccUninitialize](../extensibility/sccuninitialize-function.md)呼叫。  
  
 `lpCallerName`和`lpSccName`參數可讓在 IDE 和原始檔控制外掛程式交換名稱。 這些名稱可能只用來區別多個執行個體，或它們可能實際上會出現在功能表或對話方塊。  
  
 `lpAuxPathLabel`參數是以註解用來識別儲存的方案檔，並傳遞至原始檔控制外掛程式的呼叫中的輔助專案路徑的字串[SccOpenProject](../extensibility/sccopenproject-function.md)。 [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]會使用字串"SourceSafe 專案:";其他原始檔控制外掛程式應該避免使用這個特定的字串。  
  
 `lpSccCaps`參數可讓原始檔控制外掛程式位置以儲存位元旗標，指出 「 隨插即用單元的功能。 (如需完整的功能位元旗標清單，請參閱[功能旗標](../extensibility/capability-flags.md))。 比方說，如果將結果寫入到呼叫端提供的回呼函式，此外掛程式會設定功能的外掛程式計劃位元 SCC_CAP_TEXTOUT。 這會通知 IDE 來建立版本控制結果的視窗。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [功能旗標](../extensibility/capability-flags.md)