---
title: IScriptNode：： CreateChildEntry |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode. CreateChildEntry
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildEntry
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c58ff83c43a1418e6fb7bd8945afa181af60c68a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573609"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
加入 `IScriptEntry`的子實例。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>參數  
 `isn`  
 在父系中子系的索引。  
  
 `dwCookie`  
 在應用程式定義的值，用來將子專案與主物件產生關聯。  
  
 `pszDelimiter`  
 在結束腳本區塊分隔符號的位址。 對於剖析，主機通常會使用分隔符號（例如兩個單引號）來偵測腳本區塊的結尾。  
  
 分隔符號可讓腳本撰寫引擎提供前置處理。 例如，引擎可能會使用兩個單引號來取代單引號，以作為分隔符號。 引擎會決定分隔符號的使用方式。  
  
 如果分隔符號不會標示腳本區塊的結尾，則設定為 Null。  
  
 `ppse`  
 脫銷接收子實例之 `IScriptEntry` 介面指標的變數位址。  
  
 對於代表網頁的 `IScriptNode` 物件，此參數會傳回指定腳本區塊的 `IScriptEntry` 實例。  
  
 對於代表腳本區塊的 `IScriptEntry` 物件，此參數會傳回指定函式物件的 `IScriptEntry` 實例。  
  
 若為代表函式物件的 `IScriptEntry` 物件，這個方法會失敗。  
  
 若為 `IScriptScriptlet` 物件，這個方法會失敗。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 `IScriptNode` 介面表示網頁或其元素。 `IScriptEntry` 介面（衍生自 `IScriptNode`）代表腳本區塊或函式物件。 `IScriptScriptlet` 介面（衍生自 `IScriptEntry`）代表事件處理常式。  
  
## <a name="see-also"></a>另請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)