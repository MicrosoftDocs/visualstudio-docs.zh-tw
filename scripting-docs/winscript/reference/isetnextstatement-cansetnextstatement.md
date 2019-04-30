---
title: ISetNextStatement::CanSetNextStatement |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISetNextStatement.CanSetNextStatement
apilocation:
- scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb65faaf107c42b44201ea18c1150f8093b1654c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786611"
---
# <a name="isetnextstatementcansetnextstatement"></a>ISetNextStatement::CanSetNextStatement
這個方法會判斷是否執行點，用來決定要執行的程式碼的下一個陳述式，可以設定為指定的位置。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CanSetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### <a name="parameters"></a>參數  
 `pStackFrame`  
 [in]堆疊框架物件的指標。  
  
 `pCodeContext`  
 [in]程式碼內容物件的指標。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|下一個陳述式可以更新至指定的程式碼內容。|  
|`S_FALSE`|下一個陳述式無法更新為指定的程式碼內容中。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [ISetNextStatement 介面](../../winscript/reference/isetnextstatement-interface.md)