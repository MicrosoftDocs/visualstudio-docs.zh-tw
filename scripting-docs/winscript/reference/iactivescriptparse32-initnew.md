---
title: IActiveScriptParse32：： InitNew |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 887e4ce44662cc591fee64f5e0549edcdcbc14af
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835702"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
初始化腳本引擎。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>傳回值  
 `S_OK`如果成功，則傳回; `E_FAIL` 如果在初始化期間發生錯誤，則傳回。  
  
## <a name="remarks"></a>備註  
 您必須先呼叫下列其中一種方法，才可以使用腳本引擎： `IPersist*::Load` 、 `IPersist*::InitNew` 或 `IActiveScriptParse32::InitNew` 。 這個方法的語義與相同，因為 `IPersistStreamInit::InitNew` 這個方法會指示腳本引擎自行初始化。 請注意，呼叫或和都是無效 `IPersist*::InitNew` 的 `IActiveScriptParse32::InitNew` `IPersist*::Load` ，也不能呼叫 `IPersist*::InitNew` 、 `IActiveScriptParse32::InitNew` 或 `IPersist*::Load` 一次以上。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)