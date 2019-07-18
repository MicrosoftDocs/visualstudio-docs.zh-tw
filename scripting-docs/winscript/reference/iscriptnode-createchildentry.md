---
title: IScriptNode::CreateChildEntry |Microsoft Docs
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
ms.openlocfilehash: 75369df719b0cd140ce621e916215eb18cf30a9e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787615"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode::CreateChildEntry
新增子執行個體的`IScriptEntry`。  
  
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
 [in]與父系之子系的索引。  
  
 `dwCookie`  
 [in]應用程式定義的值，用來與主機物件關聯的子系項目。  
  
 `pszDelimiter`  
 [in]End 的指令碼區塊分隔符號的位址。 進行剖析，主應用程式通常會使用分隔符號 （例如兩個單引號），偵測到指令碼區塊的結尾。  
  
 分隔符號可以讓撰寫引擎提供前置處理指令碼。 比方說，引擎可能會取代一個單引號兩個單引號以做為分隔符號。 引擎會決定如何使用分隔符號。  
  
 如果分隔符號不會標記指令碼區塊的結尾，則設為 NULL。  
  
 `ppse`  
 [out]收到的指標變數的位址`IScriptEntry`子執行個體的介面。  
  
 針對`IScriptNode`代表網頁的物件，這個參數傳回`IScriptEntry`指定指令碼區塊的執行個體。  
  
 針對`IScriptEntry`代表的指令碼區塊的物件，這個參數傳回`IScriptEntry`指定函式物件的執行個體。  
  
 針對`IScriptEntry`物件代表的函式的物件，這個方法會失敗。  
  
 針對`IScriptScriptlet`物件，這個方法會失敗。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 `IScriptNode`介面代表網頁或其項目。 `IScriptEntry`介面 (衍生自`IScriptNode`) 代表的指令碼區塊或函式物件。 `IScriptScriptlet`介面 (衍生自`IScriptEntry`) 代表的事件處理常式。  
  
## <a name="see-also"></a>另請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)