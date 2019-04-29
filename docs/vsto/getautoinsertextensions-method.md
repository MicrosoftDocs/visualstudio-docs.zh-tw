---
title: GetAutoInsertExtensions 方法
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
ms.openlocfilehash: fb767ec7301a1d4e0f29003971b017339228fc9f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62972274"
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions 方法
  取得要在偵錯期間會自動插入的 Office 應用程式的相關資訊。

 這個方法是保留供日後使用。

## <a name="syntax"></a>語法

```csharp
HRESULT GetAutoInsertExtensions(
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames
);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*psaExtensionNames*|適用於 Office 的應用程式擴充功能名稱。|

## <a name="return-value"></a>傳回值
 HRESULT 值，表示此方法是否已順利完成。

## <a name="remarks"></a>備註
 每個要插入的 Office 應用程式以 Office 應用程式擴充功能名稱，對應到了下的值傳回**HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**。 主機必須查閱登錄中的這些值，然後再自動插入擴充功能。
