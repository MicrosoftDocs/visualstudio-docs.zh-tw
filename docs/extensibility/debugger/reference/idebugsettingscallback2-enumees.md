---
title: IDebugSettingsCallback2::EnumEEs | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::EnumEEs
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5205cfbda0420e45fc1e22dac678d97975f937a8
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212157"
---
# <a name="idebugsettingscallback2enumees"></a>IDebugSettingsCallback2::EnumEEs
列舉可用的運算式評估工具提供的語言和廠商識別碼。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumEEs(
   DWORD  celtBuffer,
   GUID*  rgguidLang,
   GUID*  rgguidVendor,
   DWORD* pceltEEs
);
```

```csharp
public int EnumEEs(
   uint       celtBuffer,
   ref Guid   rgguidLang,
   ref Guid   rgguidVendor,
   ref uint[] pceltEEs
);
```

## <a name="parameters"></a>參數
`celtBuffer`\
[in]中的項目數`pceltEEs`緩衝區。

`rgguidLang`\
[in、 out]程式設計語言的唯一識別碼。

`rgguidVendor`\
[in、 out]廠商的唯一識別碼。

`pceltEEs`\
[in、 out]運算式評估工具的陣列。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)