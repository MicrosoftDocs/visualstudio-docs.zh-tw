---
title: "IScriptNode:: CreateChildEntry |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptNode. CreateChildEntry
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildEntry
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8fcc010efe8fcf30a8f467dd94befff54bc5fac5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
將子執行個體加入`IScriptEntry`。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>參數  
 `isn`  
 [in]與父系的子系的索引。  
  
 `dwCookie`  
 [in]應用程式定義的值，將子項目和主物件產生關聯。  
  
 `pszDelimiter`  
 [in]結束的指令碼區塊分隔符號的位址。 進行剖析，主應用程式通常使用的分隔符號 （例如兩個單引號），來偵測指令碼區塊的結尾。  
  
 分隔符號，可讓撰寫引擎提供前置處理指令碼。 比方說，引擎可能會取代一個單引號兩個單引號做為分隔符號使用。 引擎會決定如何使用分隔符號。  
  
 如果分隔符號不會將標示指令碼區塊的結尾，則設為 NULL。  
  
 `ppse`  
 [out]收到的指標變數的位址`IScriptEntry`子執行個體的介面。  
  
 如`IScriptNode`代表網頁的物件，這個參數會傳回`IScriptEntry`指定指令碼區塊的執行個體。  
  
 如`IScriptEntry`代表指令碼區塊的物件，這個參數會傳回`IScriptEntry`指定函式物件的執行個體。  
  
 如`IScriptEntry`物件，表示函式物件，這個方法會失敗。  
  
 如`IScriptScriptlet`物件，這個方法會失敗。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 `IScriptNode`介面代表網頁或其項目。 `IScriptEntry`介面 (其衍生自`IScriptNode`) 代表指令碼區塊或函式物件。 `IScriptScriptlet`介面 (其衍生自`IScriptEntry`) 代表的事件處理常式。  
  
## <a name="see-also"></a>另請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)