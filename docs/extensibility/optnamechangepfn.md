---
title: "OPTNAMECHANGEPFN |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OPTNAMECHANGEPFN
helpviewer_keywords: OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2d067d5dd150dd026a2bd29a8933e8d9f72222b0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
這是在呼叫中指定的回呼函式[SccSetOption](../extensibility/sccsetoption-function.md) (使用選項`SCC_OPT_NAMECHANGEPFN`) 和用於進行通訊所做的原始檔控制外掛程式傳回給 IDE 的名稱變更。  
  
## <a name="signature"></a>簽章  
  
```cpp  
typedef void (*OPTNAMECHANGEPFN)(  
   LPVOID pvCallerData,  
   LPCSTR pszOldName,  
   LPCSTR pszNewName  
);  
```  
  
## <a name="parameters"></a>參數  
 pvCallerData  
 [in]先前呼叫中指定的使用者值[SccSetOption](../extensibility/sccsetoption-function.md) (使用選項`SCC_OPT_USERDATA`)。  
  
 pszOldName  
 [in]檔案的原始名稱。  
  
 pszNewName  
 [in]檔案的名稱已重新命名為。  
  
## <a name="return-value"></a>傳回值  
 無。  
  
## <a name="remarks"></a>備註  
 如果檔案重新命名原始檔控制作業期間，原始檔控制外掛程式會通知 IDE 需透過此回呼名稱變更。  
  
 如果在 IDE 中不支援此回呼，它不會呼叫[SccSetOption](../extensibility/sccsetoption-function.md)指定它。 如果外掛程式不支援此回呼，它會傳回`SCC_E_OPNOTSUPPORTED`從`SccSetOption`當 IDE 嘗試設定回呼函式。  
  
## <a name="see-also"></a>請參閱  
 [IDE 所實作的回呼函式](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)