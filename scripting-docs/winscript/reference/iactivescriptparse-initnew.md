---
title: 'Iactivescriptparse:: Initnew |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.InitNew
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_InitNew
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0998bea50d7839f93111aa6b116934fae35bfa3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089982"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
初始化指令碼引擎。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`如果成功，或`E_FAIL`如果在初始化期間發生錯誤。  
  
## <a name="remarks"></a>備註  
 可以使用指令碼引擎之前，其中一種下列方法必須呼叫： `IPersist*::Load`， `IPersist*::InitNew`，或`IActiveScriptParse::InitNew`。 這個方法的語意都完全相同`IPersistStreamInit::InitNew`，這個方法會告訴指令碼引擎，以將其初始化。 請注意，不用於呼叫`IPersist*::InitNew`或`IActiveScriptParse::InitNew`並`IPersist*::Load`，也不是有效地呼叫`IPersist*::InitNew`， `IActiveScriptParse::InitNew`，或`IPersist*::Load`一次以上。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)