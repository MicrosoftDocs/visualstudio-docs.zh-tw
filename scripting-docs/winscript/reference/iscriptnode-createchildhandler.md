---
title: IScriptNode::CreateChildHandler | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.CreateChildHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bca8b30021d39638f3755bace2625bb38a44242d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787140"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
將程式碼片段新增為子執行個體`IScriptNode`。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
 [in]與 scriptlet 相關聯的預設名稱的位址。  
  
 `prgpszNames`  
 [在 size_is (`cpszNames`)] 的主機上的完整限定名稱的識別項清單。  
  
 `cpszNames`  
 [in]中的識別項的數目`prgpszNames`參數。  
  
 `pszEvent`  
 [in]識別與 scriptlet 相關的事件名稱的緩衝區位址。  
  
 `pszDelimiter`  
 [in]End 的指令碼區塊分隔符號的位址。 進行剖析，主應用程式通常會使用分隔符號 （例如兩個單引號），偵測到指令碼區塊的結尾。  
  
 分隔符號會讓前置處理指令碼撰寫引擎。 比方說，引擎可能會取代一個單引號兩個單引號以做為分隔符號。 引擎會決定如何使用分隔符號。  
  
 如果沒有分隔符號用來識別指令碼區塊的結尾，則設為 NULL。  
  
 `ptiSignature`  
 [in]函式物件型別資訊。  
  
 `iMethodSignature`  
 [in]中的函式索引`ITypeInfo``ptiSignature`參數。  
  
 `isn`  
 [in]與父系之子系的索引。  
  
 `dwCookie`  
 [in]應用程式定義值，用來與主機物件關聯的項目。  
  
 `ppse`  
 [out]收到的指標變數的位址`IScriptEntry`子執行個體的介面。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 程式碼片段會指定事件處理常式。 如果它由呼叫這個方法會建立程式碼片段`IScriptNode`物件，表示 Web 網頁。 如果它由其他介面呼叫這個方法會失敗。  
  
## <a name="see-also"></a>另請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)