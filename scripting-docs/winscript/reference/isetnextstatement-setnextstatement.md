---
title: ISetNextStatement：： SetNextStatement |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISetNextStatement.SetNextStatement
apilocation:
- scrobj.dll
ms.assetid: c5534f3b-39a5-4466-b8fc-69b717c6eee9
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e8b940e603deb0aa9715e89b49eb1afdd28832ac
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571903"
---
# <a name="isetnextstatementsetnextstatement"></a>ISetNextStatement::SetNextStatement
這個方法會更新腳本解譯器可執行檔下一個程式碼內容。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### <a name="parameters"></a>參數  
 `pStackFrame`  
 在堆疊框架物件的指標。  
  
 `pCodeContext`  
 在程式碼內容物件的指標。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [ISetNextStatement 介面](../../winscript/reference/isetnextstatement-interface.md)