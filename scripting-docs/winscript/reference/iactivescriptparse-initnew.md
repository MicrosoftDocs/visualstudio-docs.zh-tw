---
title: "IActiveScriptParse::InitNew |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptParse.InitNew
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_InitNew
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e34094bcc25c0316fa670f570d8b2664acc0ba78
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
初始化指令碼引擎。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`如果成功，或`E_FAIL`如果在初始化期間發生錯誤。  
  
## <a name="remarks"></a>備註  
 可以使用指令碼引擎之前，下列方法之一必須呼叫： `IPersist*::Load`， `IPersist*::InitNew`，或`IActiveScriptParse::InitNew`。 這個方法的語意都完全相同`IPersistStreamInit::InitNew`、，這個方法會告訴初始化本身的指令碼引擎。 請注意，不能呼叫兩者`IPersist*::InitNew`或`IActiveScriptParse::InitNew`和`IPersist*::Load`，也不是有效呼叫`IPersist*::InitNew`， `IActiveScriptParse::InitNew`，或`IPersist*::Load`一次以上。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)