---
title: ScriptEngineBuildVersion 函式 (JavaScript) |Microsoft 文件
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
- ScriptEngineBuildVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ScriptEngineBuildVersion function
ms.assetid: 7e255030-b0a3-420b-9c96-bb3e93c9333f
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd458d43bebfb0d0e0b2cb6bebb483c22a60b4f0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640018"
---
# <a name="scriptenginebuildversion-function-javascript"></a>ScriptEngineBuildVersion 函式 (JavaScript)
取得使用中指令碼引擎的組建版本號碼。  
  
## <a name="syntax"></a>語法  
  
```  
ScriptEngineBuildVersion()  
```  
  
## <a name="remarks"></a>備註  
 傳回值直接對應到使用中指令碼語言的動態連結程式庫 (DLL) 中所含的版本資訊。  
  
## <a name="example"></a>範例  
 下面範例說明如何使用 `ScriptEngineBuildVersion` 函式：  
  
```JavaScript  
if(window.ScriptEngineBuildVersion) {  
    console.log(window.ScriptEngineBuildVersion());  
}  
  
// Output: <current build version>  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ScriptEngine 函式](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineMajorVersion 函式](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [ScriptEngineMinorVersion 函式](../../javascript/reference/scriptengineminorversion-function-javascript.md)