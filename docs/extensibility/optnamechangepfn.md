---
title: OPTNAMECHANGEPFN |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 083b91dd44101f387c89e2313dba3ffb9a9ee737
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636512"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
這是呼叫中指定的回呼函式[SccSetOption](../extensibility/sccsetoption-function.md) (使用選項`SCC_OPT_NAMECHANGEPFN`) 並且用來傳達名稱所做的變更原始檔控制外掛程式傳回給 IDE。  
  
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
 [in]檔案名稱已重新命名為。  
  
## <a name="return-value"></a>傳回值  
 無。  
  
## <a name="remarks"></a>備註  
 如果檔案已重新命名原始檔控制作業期間，原始檔控制外掛程式可以通知名稱變更，透過此回呼中相關的 IDE。  
  
 IDE 不支援此回呼中，如果它不會呼叫[SccSetOption](../extensibility/sccsetoption-function.md)加以指定。 如果外掛程式不支援此回呼中，它會傳回`SCC_E_OPNOTSUPPORTED`從`SccSetOption`函式時，IDE 會嘗試回呼。  
  
## <a name="see-also"></a>另請參閱  
 [IDE 所實作的回呼函式](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)