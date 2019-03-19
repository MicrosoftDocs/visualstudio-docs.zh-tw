---
title: IActiveScriptErrorDebug110::GetExceptionThrownKind |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug110::QueryIsFirstChance
ms.assetid: ecc16e54-93e4-4322-ae13-afa7cd860032
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61f045348add6ba9595bc93ff48dc2d35498016a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145508"
---
# <a name="iactivescripterrordebug110getexceptionthrownkind"></a>IActiveScriptErrorDebug110::GetExceptionThrownKind
傳回會指出擲回的例外狀況類型的值。  
  
> [!IMPORTANT]
>  [IActiveScriptErrorDebug110 介面](../../winscript/reference/iactivescripterrordebug110-interface.md)由 PDM 11.0 和更新版本所實作。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetExceptionThrownKind(  
   SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND*  pExceptionKind  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pExceptionKind`  
 [out]所表示的 （例如，第一個可能發生或未處理），就會擲回的例外狀況種類[SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND 列舉](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md)列舉值。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptErrorDebug110 介面](../../winscript/reference/iactivescripterrordebug110-interface.md)