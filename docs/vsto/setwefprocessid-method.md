---
title: SetWefProcessId 方法
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 13a6748e2e3b66f581a3c72c1f847e0329189e64
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537328"
---
# <a name="setwefprocessid-method"></a>SetWefProcessId 方法
  提供將執行 Web Extensions Framework （WEF）內容的處理序識別碼。

## <a name="syntax"></a>語法

```csharp
HRESULT SetWefProcessId(
    [in] DWORD dwProcessId
);
```

#### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*dwProcessId*|將用來執行 WEF 內容的處理序識別碼。|

## <a name="return-value"></a>傳回值
 HRESULT 值，表示此方法是否已順利完成。

## <a name="remarks"></a>備註
 在建立 WEF 內容程式之後，但在任何 WEF 內容執行之前，都必須呼叫這個方法。

 如果您想要開發環境將偵錯工具附加至 WEF 內容進程，則環境必須在此方法的實作為執行此作業。
