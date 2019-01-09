---
title: JS_PROPERTY_MEMBERS 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_PROPERTY_MEMBERS
apilocation:
- jscript9diag.dll
ms.assetid: 3b870e5c-5518-4073-8384-f0c9c1777d9e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57d933a86d5ffe8d2b8aec243b5eb6bd2ae93a59
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096826"
---
# <a name="jspropertymembers-enumeration"></a>JS_PROPERTY_MEMBERS 列舉
旗標，用於指定在物件成員的要求中傳回的資訊類型。  
  
## <a name="syntax"></a>語法  
  
```cpp
enum JS_PROPERTY_MEMBERS{   JS_PROPERTY_MEMBERS_ALL = 0,   JS_PROPERTY_MEMBERS_ARGUMENTS = 1} JS_PROPERTY_MEMBERS;  
```  
  
## <a name="members"></a>成員  
  
### <a name="values"></a>值  
  
|名稱|描述|  
|----------|-----------------|  
|`JS_PROPERTY_MEMBERS_ALL`|代表要列舉所有成員的要求。|  
|`JS_PROPERTY_MEMBERS_ARGUMENTS`|表示列舉引數僅要求。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)