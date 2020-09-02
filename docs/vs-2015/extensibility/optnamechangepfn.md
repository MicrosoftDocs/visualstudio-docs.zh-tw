---
title: OPTNAMECHANGEPFN |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4969dff811b6517c0274a35884703a9dc0c693cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194097"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

這是在 [SccSetOption](../extensibility/sccsetoption-function.md) (中指定的回呼函式，其使用選項 `SCC_OPT_NAMECHANGEPFN`) ，並且用來將原始檔控制外掛程式所做的名稱變更傳遞回 IDE。  
  
## <a name="signature"></a>簽章  
  
```cpp#  
typedef void (*OPTNAMECHANGEPFN)(  
   LPVOID pvCallerData,  
   LPCSTR pszOldName,  
   LPCSTR pszNewName  
);  
```  
  
## <a name="parameters"></a>參數  
 pvCallerData  
 在先前呼叫 [SccSetOption](../extensibility/sccsetoption-function.md) (中指定的使用者值，) 使用選項 `SCC_OPT_USERDATA` 。  
  
 pszOldName  
 在檔案的原始名稱。  
  
 pszNewName  
 在檔案已重新命名為的名稱。  
  
## <a name="return-value"></a>傳回值  
 無。  
  
## <a name="remarks"></a>備註  
 如果檔案在原始檔控制作業期間重新命名，原始檔控制外掛程式可透過此回呼通知 IDE 有關名稱變更。  
  
 如果 IDE 不支援此回呼，則不會呼叫 [SccSetOption](../extensibility/sccsetoption-function.md) 來指定它。 如果外掛程式不支援此回呼，則 `SCC_E_OPNOTSUPPORTED` `SccSetOption` 當 IDE 嘗試設定回呼時，它會從函式傳回。  
  
## <a name="see-also"></a>另請參閱  
 [IDE 所執行的回呼函數](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)
