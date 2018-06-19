---
title: ScriptEngineMajorVersion 函式 (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ScriptEngineMajorVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ScriptEngineMajorVersion function
ms.assetid: 3e251bce-1e14-4cb5-b79f-53845d1920fd
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 815e6fb92744fc2145cae2cbaa6a5574c3ea3ecc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639678"
---
# <a name="scriptenginemajorversion-function-javascript"></a>ScriptEngineMajorVersion 函式 (JavaScript)
取得使用中指令碼引擎的主要版本號碼。  
  
## <a name="syntax"></a>語法  
  
```  
ScriptEngineMajorVersion()  
```  
  
## <a name="remarks"></a>備註  
 傳回值直接對應到使用中指令碼語言的動態連結程式庫 (DLL) 中所含的版本資訊。  
  
## <a name="example"></a>範例  
 下面範例說明如何使用 `ScriptEngineMajorVersion` 函式：  
  
```JavaScript  
if (window.ScriptEngineMajorVersion) {  
    console.log(window.ScriptEngine());   
}  
  
Output: <current major version>  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ScriptEngine 函式](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineBuildVersion 函式](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMinorVersion 函式](../../javascript/reference/scriptengineminorversion-function-javascript.md)