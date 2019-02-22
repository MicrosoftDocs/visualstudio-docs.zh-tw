---
title: IActiveScript::AddTypeLib |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_AddTypeLib
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 695edbd6f5356959785e54dc38f28b68c8c0400e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092536"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
將指令碼的命名空間中的型別程式庫。 這是類似於`#include`C/c + + 指示詞。 它可讓一組預先定義的項目類別定義，例如`typedefs`，與具名常數可以加入至可供指令碼的執行階段環境。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `guidTypeLib`  
 [in]將類型程式庫的 CLSID。  
  
 `dwMaj`  
 [in]主要版本號碼。  
  
 `dwMin`  
 [in]次要版本號碼。  
  
 `dwFlags`  
 [in]選項旗標。 可以是下列：  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|型別程式庫描述主機所使用的 ActiveX 控制項。|  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_UNEXPECTED`|不需要呼叫 （例如，指令碼引擎有尚未載入或初始化）。|  
|`TYPE_E_CANTLOADLIBRARY`|無法載入指定的型別程式庫。|  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)