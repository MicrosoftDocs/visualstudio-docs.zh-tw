---
title: GetVstoSolutionMetadata 函式
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
ms.openlocfilehash: d7714e78e897e6c8b391a6c30e9a548671ce80c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796037"
---
# <a name="getvstosolutionmetadata-function"></a>GetVstoSolutionMetadata 函式
  此 API 支援 Office 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```csharp
HRESULT WINAPI GetVstoSolutionMetadata(
    LPCWSTR lpwszSolutionMetadataKey,
    ISolutionMetadata** ppSolutionInfo
);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*lpwszSolutionMetadataKey*|請勿使用。|
|*ppSolutionInfo*|請勿使用。|

## <a name="return-value"></a>傳回值
 如果此函數就會成功，它會傳回**S_OK**。 如果函式失敗，它會傳回錯誤碼。
