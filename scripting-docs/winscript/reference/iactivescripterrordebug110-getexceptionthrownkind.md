---
title: IActiveScriptErrorDebug110::GetExceptionThrownKind |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ce3a164f3ee4d81ca849db7c4745948ffe17d56e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097184"
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