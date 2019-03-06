---
title: IDebugCodeContext2::GetLanguageInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4afcb2a8fd9de89b74fccec373e71e19264fe56
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56712485"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
取得此程式碼內容的語言資訊。

## <a name="syntax"></a>語法

```cpp
HRESULT GetLanguageInfo( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo( 
   ref string pbstrLanguage,
   ref Guid pguidLanguage
);
```

#### <a name="parameters"></a>參數
 `pbstrLanguage`

 [in、 out]傳回字串，包含名稱的語言，例如"C + +"。

 `pguidLanguage`

 [in、 out]例如，傳回之語言的程式碼內容，GUID `guidCPPLang`。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 至少其中一個參數必須傳回非 null 值。

## <a name="see-also"></a>另請參閱
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)