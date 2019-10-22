---
title: ISetNextStatement：： CanSetNextStatement |Microsoft Docs
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
ms.openlocfilehash: 56cf0b2e4afd7a86a087b37be4b23758a5b59720
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571850"
---
# <a name="isetnextstatementcansetnextstatement"></a>ISetNextStatement::CanSetNextStatement
這個方法會決定是否可以將執行點（判斷下一個要執行的程式碼語句）設定為指定的位置。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CanSetNextStatement(  
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
|`S_OK`|下一個語句可以更新為指定的程式碼內容。|  
|`S_FALSE`|下一個語句無法更新為指定的程式碼內容。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [ISetNextStatement 介面](../../winscript/reference/isetnextstatement-interface.md)