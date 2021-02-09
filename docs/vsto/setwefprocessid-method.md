---
title: SetWefProcessId 方法
description: 瞭解 SetWefProcessId 方法如何提供處理序識別碼，以 (WEF) 內容來執行 Web Extensions Framework。
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
ms.openlocfilehash: 9c3d745f14185d46dce08d46b8c56391b108627d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882404"
---
# <a name="setwefprocessid-method"></a>SetWefProcessId 方法
  提供將執行 Web Extensions Framework (WEF) 內容的處理序識別碼。

## <a name="syntax"></a>語法

```csharp
HRESULT SetWefProcessId(
    [in] DWORD dwProcessId
);
```

#### <a name="parameters"></a>參數

|參數|Description|
|---------------|-----------------|
|*dwProcessId*|將用來執行 WEF 內容的處理序識別碼。|

## <a name="return-value"></a>傳回值
 HRESULT 值，表示此方法是否已順利完成。

## <a name="remarks"></a>備註
 在建立 WEF 內容程式之後，但在任何 WEF 內容執行之前，必須呼叫這個方法。

 如果您想要讓開發環境將偵錯工具附加至 WEF 內容處理常式，環境必須在此方法的實執行中執行此作業。
