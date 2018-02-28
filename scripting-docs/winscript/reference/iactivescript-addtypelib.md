---
title: "IActiveScript::AddTypeLib |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_AddTypeLib
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2be7cf033b4b5dd4d99b19a3b71ed53e32af855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
將類型程式庫加入至指令碼的命名空間。 這是類似於`#include`C/c + + 中的指示詞。 它可讓一組預先定義的項目類別定義，例如`typedefs`，和名為要加入至執行階段環境的指令碼中使用的常數。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `guidTypeLib`  
 [in]若要加入類型程式庫的 CLSID。  
  
 `dwMaj`  
 [in]主要版本號碼。  
  
 `dwMin`  
 [in]次要版本號碼。  
  
 `dwFlags`  
 [in]選項旗標。 可以是下列：  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|類型程式庫描述主機使用的 ActiveX 控制項。|  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_UNEXPECTED`|不應該呼叫 （例如，指令碼引擎有尚未載入或初始化）。|  
|`TYPE_E_CANTLOADLIBRARY`|無法載入指定的型別程式庫。|  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)