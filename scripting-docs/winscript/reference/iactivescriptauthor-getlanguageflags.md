---
title: IActiveScriptAuthor：： GetLanguageFlags |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 68da16513050bd87642be2c96212a330a0916608
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576194"
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
傳回語言資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pgrfasa`  
 脫銷包含語言資訊的旗標。 可以是下列值的組合：  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0x0001|語言偏好由腳本撰寫引擎（而非應用程式）所建立的腳本事件處理常式。|  
|fasaSupportInternalHandler|0x0002|語言支援腳本撰寫引擎所建立的腳本事件處理常式。|  
|fasaCaseSensitive|0x0004|指令碼語言會區分大小寫。|  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 如果腳本撰寫引擎會管理事件處理常式，則您的應用程式應該從 `IScriptEntry` 物件呼叫 `CreateChildHandler`。 這會建立一個對應于事件處理常式的 `IScriptScriptlet` 物件。 引擎也會將事件處理常式加入至腳本專案。 事件處理常式是空的函式，其中包含指定的簽章資訊。  
  
 如果您的應用程式管理事件處理常式，則應該從代表事件處理常式程式碼片段的 `IScriptNode` 物件呼叫 `CreateChildHandler`。 這會建立與事件處理常式程式碼片段相關聯的 `IScriptScriptlet` 物件。 應用程式也必須將空的函式當做事件處理常式加入至新的或現有的 `IScriptEntry` 物件。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)