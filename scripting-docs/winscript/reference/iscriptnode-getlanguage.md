---
title: IScriptNode：： GetLanguage |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetLanguage
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetLanguage
ms.assetid: 089715fd-6746-474e-94ed-2e57ee4bc0da
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26fd5db22346292585be3cea751eaa8be1c284a9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575687"
---
# <a name="iscriptnodegetlanguage"></a>IScriptNode::GetLanguage
傳回目前腳本節點所使用的指令碼語言。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetLanguage(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstr`  
 脫銷如果腳本節點使用 JScript，則傳回「JScript」，如果腳本節點使用 Visual Basic Scripting Edition （VBScript），則傳回「VBScript」。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)