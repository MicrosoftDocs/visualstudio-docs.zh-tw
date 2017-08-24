---
title: IDebugOutputStringEvent2::GetString | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugOutputStringEvent2::GetString
helpviewer_keywords:
- IDebugOutputStringEvent2::GetString
ms.assetid: f059f8e0-ad44-49ac-ba90-73576ada5e06
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: ddcc17c18f4e11d90e252e248c0447330a8c31f0
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugoutputstringevent2getstring"></a>IDebugOutputStringEvent2::GetString
Gets the displayable message.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetString(   
   BSTR* pbstrString  
);  
```  
  
```cs  
int GetString(   
   out string pbstrString  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pbstrString`  
 [out] Returns the displayable message.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="see-also"></a>See Also  
 [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)
