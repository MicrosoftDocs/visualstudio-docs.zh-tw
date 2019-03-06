---
title: IDebugProgramProvider2::SetLocale | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::SetLocale
helpviewer_keywords:
- IDebugProgramProvider2::SetLocale
ms.assetid: b41d20a7-ba40-4c42-a450-16f413d6a04f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a9a7d31f7ac442f4a6ff529ae46f1f7492665211
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722300"
---
# <a name="idebugprogramprovider2setlocale"></a>IDebugProgramProvider2::SetLocale
建立要用於任何地區設定特定資源的地區設定。

## <a name="syntax"></a>語法

```cpp
HRESULT SetLocale(
   WORD wLangID
);
```

```csharp
int SetLocale(
   ushort wLangID
);
```

#### <a name="parameters"></a>參數
 `wLangID`

 [in]若要建立的語言識別碼。 例如，1033 代表英文。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)