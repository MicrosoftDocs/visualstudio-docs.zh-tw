---
title: IScriptEntry::GetBody |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetBody
ms.assetid: 419c8c11-a1f8-4b97-ab00-e8af2b2f9bfc
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b5eb878bccaa8ed415fd813095e31064bc7e245
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094808"
---
# <a name="iscriptentrygetbody"></a>IScriptEntry::GetBody
傳回對應的文字本文`IScriptEntry`指令碼區塊、 函式區塊或程式碼片段。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstr`  
 [out]本文的下列其中一種文字：  
  
-   `IScriptEntry`指令碼區塊  
  
-   `IScriptEntry`函式區塊中的函式  
  
-   `IScriptEntry` Scriptlet 事件處理常式  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)