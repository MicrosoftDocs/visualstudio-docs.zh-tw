---
title: IActiveScriptParse32：： InitNew |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 8b5304d60aed8145e7a68d89b2c6d4386db0d745
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561655"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32：： InitNew
初始化腳本引擎。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`，如果初始化期間發生錯誤，則傳回 `E_FAIL`。  
  
## <a name="remarks"></a>備註  
 您必須先呼叫下列其中一種方法，才可以使用腳本引擎： `IPersist*::Load`、`IPersist*::InitNew` 或 `IActiveScriptParse32::InitNew`。 這個方法的語義與 `IPersistStreamInit::InitNew` 相同，因為這個方法會指示腳本引擎自行初始化。 請注意，呼叫 `IPersist*::InitNew` 或 `IActiveScriptParse32::InitNew` 和 `IPersist*::Load` 都是不正確，也不能對 `IPersist*::InitNew`、`IActiveScriptParse32::InitNew` 或 `IPersist*::Load` 多次呼叫。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)