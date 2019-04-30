---
title: SetWefProcessId 方法
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
ms.openlocfilehash: 1352ccc9318061be4a2f9ad2da7d63715acd6721
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978350"
---
# <a name="setwefprocessid-method"></a>SetWefProcessId 方法
  提供將執行 Web 擴充功能架構 (WEF) 內容的處理序識別碼。

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
 建立 WEF 內容處理程序之後，但任何 WEF 內容執行之前，必須呼叫這個方法。

 如果您想要將偵錯工具附加至 WEF 內容處理程序的開發環境，環境就必須實作這個方法中執行此作業。
