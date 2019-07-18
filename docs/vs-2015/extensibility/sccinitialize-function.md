---
title: SccInitialize 函式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ce52b65d028f82d75d4890b0b1298b4d13b7eafa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200031"
---
# <a name="sccinitialize-function"></a>SccInitialize 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此函式會初始化原始檔控制外掛程式，並提供功能和整合式的開發環境 (IDE) 的限制。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 [in]原始檔控制外掛程式可以在此放置其內容結構的指標。  
  
 `hWnd`  
 [in]原始檔控制外掛程式時，可以使用當做父代上，它會提供任何對話方塊 IDE 視窗的控制代碼。  
  
 `lpCallerName`  
 [in]呼叫的原始檔控制外掛程式的程式名稱。  
  
 `lpSccName`  
 [in、 out]緩衝區的原始檔控制外掛程式，將自己的名稱 (不能超過`SCC_NAME_LEN`)。  
  
 `lpSccCaps`  
 [out]傳回原始檔控制外掛程式功能旗標。  
  
 `lpAuxPathLabel`  
 [in、 out]原始檔控制外掛程式的字串，描述的放置位置的緩衝區`lpAuxProjPath`所傳回的參數[SccOpenProject](../extensibility/sccopenproject-function.md)並[SccGetProjPath](../extensibility/sccgetprojpath-function.md) (不能超過`SCC_AUXLABEL_LEN`)。  
  
 `pnCheckoutCommentLen`  
 [out]傳回所允許的最大長度，簽出註解。  
  
 `pnCommentLen`  
 [out]傳回其他註解的最大允許長度。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|說明|  
|-----------|-----------------|  
|SCC_OK|原始檔控制初始化成功。|  
|SCC_E_INITIALIZEFAILED|系統無法初始化。|  
|SCC_E_NOTAUTHORIZED|不允許使用者執行指定的作業。|  
|SCC_E_NONSPECFICERROR|不明確的失敗;未初始化原始檔控制系統。|  
  
## <a name="remarks"></a>備註  
 第一次載入原始檔控制外掛程式時，IDE 就會呼叫此函式。 它可讓 IDE 傳遞特定資訊，例如，呼叫者的名稱、 給外掛程式。 IDE 也會取得回特定的資訊，例如註解及隨插即用中的功能的允許長度上限。  
  
 `ppvContext`指向`NULL`指標。 原始檔控制外掛程式可以配置供自身使用的結構，並將儲存在該結構的指標`ppvContext`。 IDE 會將這個指標傳遞至每個其他 VSSCI API 函式允許外掛程式有可用的內容資訊而不需使用全域儲存體，並支援多個外掛程式執行個體。 此結構應該要解除配置時[SccUninitialize](../extensibility/sccuninitialize-function.md)呼叫。  
  
 `lpCallerName`和`lpSccName`參數可讓 IDE，以及原始檔控制外掛程式交換名稱。 這些名稱可用來區別多個執行個體，或它們可能會實際顯示在功能表或對話方塊。  
  
 `lpAuxPathLabel`參數是字串，用為註解來識別儲存在方案檔，並傳遞至原始檔控制外掛程式的呼叫中的輔助專案路徑[SccOpenProject](../extensibility/sccopenproject-function.md)。 [!INCLUDE[vsvss](../includes/vsvss-md.md)] 會使用字串"SourceSafe 專案:";其他原始檔控制外掛程式應該避免使用這個特定的字串。  
  
 `lpSccCaps`參數可讓原始檔控制外掛程式位置以儲存位元旗標，指出隨插即用中的功能。 (如功能位元旗標完整清單，請參閱[功能旗標](../extensibility/capability-flags.md))。 比方說，如果外掛程式的計劃，將結果寫入至呼叫端提供的回呼函式，外掛程式會設定此功能，將位元 SCC_CAP_TEXTOUT。 這會指示 IDE 建立版本控制結果的視窗。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [功能旗標](../extensibility/capability-flags.md)
