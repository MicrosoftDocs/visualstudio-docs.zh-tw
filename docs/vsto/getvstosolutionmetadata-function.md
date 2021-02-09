---
title: GetVstoSolutionMetadata 函式
description: 瞭解 GetVstoSolutionMetadata API 如何支援 Office 基礎結構，而且不適合直接從程式碼使用。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: eaf58f312afd379fb1f16d208c323777ec725231
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860603"
---
# <a name="getvstosolutionmetadata-function"></a>GetVstoSolutionMetadata 函式
  此 API 支援 Office 基礎結構，而且不適合直接從程式碼使用。

## <a name="syntax"></a>語法

```csharp
HRESULT WINAPI GetVstoSolutionMetadata(
    LPCWSTR lpwszSolutionMetadataKey,
    ISolutionMetadata** ppSolutionInfo
);
```

### <a name="parameters"></a>參數

|參數|Description|
|---------------|-----------------|
|*lpwszSolutionMetadataKey*|請勿使用。|
|*ppSolutionInfo*|請勿使用。|

## <a name="return-value"></a>傳回值
 如果函式成功，它會傳回 **S_OK**。 如果函式失敗，則會傳回錯誤碼。
