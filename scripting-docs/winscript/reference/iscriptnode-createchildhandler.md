---
title: "IScriptNode::CreateChildHandler |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptNode.CreateChildHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff2ba40d1570e23f0256bd34ca8aff0f8d77ce5c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
將程式碼片段加入作為子執行個體`IScriptNode`。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszDefaultName`  
 [in]使用程式碼片段相關聯的預設名稱的位址。  
  
 `prgpszNames`  
 [在 size_is (`cpszNames`)] 的主機上的完整限定名稱的識別項清單。  
  
 `cpszNames`  
 [in]中的識別項的數目`prgpszNames`參數。  
  
 `pszEvent`  
 [in]識別程式碼片段相關聯的事件名稱的緩衝區位址。  
  
 `pszDelimiter`  
 [in]結束的指令碼區塊分隔符號的位址。 進行剖析，主應用程式通常使用的分隔符號 （例如兩個單引號），來偵測指令碼區塊的結尾。  
  
 分隔符號，可讓前置處理指令碼撰寫引擎。 比方說，引擎可能會取代一個單引號兩個單引號做為分隔符號使用。 引擎會決定如何使用分隔符號。  
  
 如果沒有分隔符號用來識別指令碼區塊的結尾，則設為 NULL。  
  
 `ptiSignature`  
 [in]函式物件類型資訊。  
  
 `iMethodSignature`  
 [in]索引中的函式`ITypeInfo``ptiSignature`參數。  
  
 `isn`  
 [in]與父系的子系的索引。  
  
 `dwCookie`  
 [in]應用程式定義值，用來將項目與主應用程式物件產生關聯。  
  
 `ppse`  
 [out]收到的指標變數的位址`IScriptEntry`子執行個體的介面。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 程式碼片段會指定事件處理常式。 如果它由呼叫這個方法會建立程式碼片段`IScriptNode`物件，代表網頁。 如果其他介面呼叫此方法不會成功。  
  
## <a name="see-also"></a>另請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)