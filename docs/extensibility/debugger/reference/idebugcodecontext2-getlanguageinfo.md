---
description: 取得此程式碼內容的語言資訊。
title: IDebugCodeCoNtext2：： GetLanguageInfo |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62d076a2780ab8d49f79379111eaeef9dd1cdc88
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088376"
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

## <a name="parameters"></a>參數
`pbstrLanguage`\
[in，out]傳回字串，其中包含語言的名稱，例如 "c + +"。

`pguidLanguage`\
[in，out]傳回程序代碼內容語言的 GUID，例如 `guidCPPLang` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 至少有一個參數必須傳回非 null 的值。

## <a name="see-also"></a>另請參閱
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
