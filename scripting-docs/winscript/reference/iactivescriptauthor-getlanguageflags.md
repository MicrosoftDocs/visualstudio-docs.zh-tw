---
title: IActiveScriptAuthor::GetLanguageFlags |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetLanguageFlags
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetLanguageFlags
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dca878d6d4fd15db4b516e37932fbfebd30607a2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093193"
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
傳回語言的資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
|fasaSupportInternalHandler|0x0002|語言支援在指令碼撰寫引擎指令碼所建立的事件處理常式。|  
|fasaCaseSensitive|0x0004|指令碼語言會區分大小寫。|  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 如果指令碼撰寫引擎管理事件處理常式，您的應用程式應該呼叫`CreateChildHandler`從`IScriptEntry`物件。 這會建立`IScriptScriptlet`與事件處理常式對應的物件。 引擎也會將事件處理常式加入至指令碼項目中。 事件處理常式會是空白的函式，其中包含指定的簽章資訊。  
  
 如果您的應用程式管理的事件處理常式，它應該呼叫`CreateChildHandler`從`IScriptNode`物件，表示事件處理常式的程式碼片段。 這會建立`IScriptScriptlet`事件處理常式程式碼片段相關聯的物件。 應用程式也必須新增空白函式，為事件處理常式，以新的或現有的`IScriptEntry`物件。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)