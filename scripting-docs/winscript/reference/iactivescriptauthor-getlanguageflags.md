---
title: "IActiveScriptAuthor::GetLanguageFlags |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetLanguageFlags
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetLanguageFlags
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6137f1cd77d2f305a9ff9d51ac49c214e4c4237b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
傳回語言資訊。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pgrfasa`  
 [out]包含語言資訊的旗標。 可以是下列值的組合：  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0x0001|語言偏好撰寫引擎，而不是應用程式的指令碼的指令碼建立事件處理常式。|  
|fasaSupportInternalHandler|0x0002|語言支援指令碼撰寫引擎所建立的指令碼事件處理常式。|  
|fasaCaseSensitive|0x0004|指令碼語言會區分大小寫。|  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 如果指令碼引擎的撰寫管理事件處理常式，您的應用程式應該呼叫`CreateChildHandler`從`IScriptEntry`物件。 這會建立`IScriptScriptlet`對應至事件處理常式的物件。 引擎也會將事件處理常式加入至指令碼項目。 此事件處理常式會是空白的函式，其中包含指定的簽章資訊。  
  
 如果您的應用程式管理事件處理常式，它應該呼叫`CreateChildHandler`從`IScriptNode`物件，代表事件處理常式的程式碼片段。 這會建立`IScriptScriptlet`事件處理常式程式碼片段相關聯的物件。 應用程式也必須加入空白的函式，為事件處理常式，以新的或現有的`IScriptEntry`物件。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)