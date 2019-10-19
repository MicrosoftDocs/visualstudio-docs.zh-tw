---
title: IActiveScript：： AddTypeLib |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 254a5133d42689020eaaae290a1016de4b848100
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575815"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
將類型程式庫加入至腳本的命名空間。 這類似于 C/C++中的 `#include` 指示詞。 它允許將一組預先定義的專案（例如類別定義、`typedefs` 和命名常數）加入至腳本可用的執行時間環境。  
  
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
 在要加入之類型程式庫的 CLSID。  
  
 `dwMaj`  
 在主要版本號碼。  
  
 `dwMin`  
 在次要版本號碼。  
  
 `dwFlags`  
 在選項旗標。 可以是下列內容：  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|類型程式庫描述主機所使用的 ActiveX 控制項。|  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一個值：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_UNEXPECTED`|不需要呼叫（例如，腳本引擎尚未載入或初始化）。|  
|`TYPE_E_CANTLOADLIBRARY`|無法載入指定的類型程式庫。|  
  
## <a name="see-also"></a>請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)