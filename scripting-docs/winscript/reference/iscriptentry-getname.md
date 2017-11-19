---
title: "IScriptEntry::GetName |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.GetName
apilocation: scrobj.dll
helpviewer_keywords: IScriptEntry::GetName
ms.assetid: 56daa288-618f-497c-a360-7d443afd478b
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc518e87414d051e9b1393b60b5874a0204b78b2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygetname"></a>IScriptEntry::GetName
表示單一物件 （例如函式） 的項目，傳回的物件名稱。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstr`  
 [out]所表示之物件的名稱`IScriptEntry`指令碼區塊。 如果項目不代表單一物件，則傳回 NULL。  
  
 子系項目代表單一函式物件。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)