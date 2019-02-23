---
title: IDebugStackFrame2::GetLanguageInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 90fd7beabb14163558afe4b957d95635e91f904a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719544"
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo
取得此堆疊框架相關聯的語言。

## <a name="syntax"></a>語法

```cpp
HRESULT GetLanguageInfo ( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo ( 
   ref string pbstrLanguage,
   ref Guid   pguidLanguage
);
```

#### <a name="parameters"></a>參數
 `pbstrLanguage`

 [out]傳回實作的方法，此堆疊框架相關聯的語言名稱。

 `pguidLanguage`

 [out]傳回`GUID`的語言。 針對[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]語言，例如，下列可傳回：

-   `guidVBScriptLang`

-   `guidJScriptLang`

-   `guidCPPLang`

-   `guidVBLang`

-   `guidSQLLang`

-   `guidScriptLang`

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)