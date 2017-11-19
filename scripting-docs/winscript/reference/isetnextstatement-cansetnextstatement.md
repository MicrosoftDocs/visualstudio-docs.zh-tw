---
title: "ISetNextStatement::CanSetNextStatement |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ISetNextStatement.CanSetNextStatement
apilocation: scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bd32ddf73076f9e29ca3377186ff64be256b8fc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="isetnextstatementcansetnextstatement"></a>ISetNextStatement::CanSetNextStatement
這個方法會判斷是否執行點，用來決定要執行的程式碼的下一個陳述式，可以設定為指定的位置。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CanSetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### <a name="parameters"></a>參數  
 `pStackFrame`  
 [in]堆疊框架物件指標。  
  
 `pCodeContext`  
 [in]程式碼的內容物件指標。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|下一個陳述式可更新為指定的程式碼內容。|  
|`S_FALSE`|下一個陳述式無法更新為指定的程式碼內容。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [ISetNextStatement 介面](../../winscript/reference/isetnextstatement-interface.md)