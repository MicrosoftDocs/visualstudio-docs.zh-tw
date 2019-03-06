---
title: GetValidCompatibleFramework 函式
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b975a4b4b2c1b4ae3f6ef0f1d6d23769bb4c77c7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56643505"
---
# <a name="getvalidcompatibleframework-function"></a>GetValidCompatibleFramework 函式
  此 API 支援 Office 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```csharp
HRESULT WINAPI GetValidCompatibleFramework(
    LPCWSTR lpwszCompatibleFrameworksXML,
    BSTR* pbstrValidFrameworkTag
);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*lpwszCompatibleFrameworksXML*|請勿使用。|
|*pbstrValidFrameworkTag*|請勿使用。|

## <a name="return-value"></a>傳回值
 如果此函數就會成功，它會傳回**S_OK**。 如果函式失敗，它會傳回錯誤碼。
