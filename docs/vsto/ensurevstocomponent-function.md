---
title: EnsureVSTOComponent 函式
description: 瞭解 EnsureVSTOComponent API 如何支援 Office 基礎結構，而且不適合直接從程式碼使用。
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
ms.openlocfilehash: 17f52a469d93a843ef776c125e15a37db22277e8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910479"
---
# <a name="ensurevstocomponent-function"></a>EnsureVSTOComponent 函式
  此 API 支援 Office 基礎結構，而且不適合直接從程式碼使用。

## <a name="syntax"></a>語法

```csharp
HRESULT EnsureVSTOComponent(
    IVSTProject *pProject
);
```

#### <a name="parameters"></a>參數

|參數|Description|
|---------------|-----------------|
|*pProject*|請勿使用。|

## <a name="return-value"></a>傳回值
 如果函式成功，它會傳回 **S_OK**。 如果函式失敗，則會傳回錯誤碼。
