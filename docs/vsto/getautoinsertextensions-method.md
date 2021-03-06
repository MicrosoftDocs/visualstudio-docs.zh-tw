---
description: 取得要在進行偵錯工具時自動插入的 Office 相關應用程式的相關資訊。
title: GetAutoInsertExtensions 方法
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
ms.openlocfilehash: c4a49942f50a79db604d2363cf2d85762c5ddce5
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223429"
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions 方法
  取得要在進行偵錯工具時自動插入的 Office 相關應用程式的相關資訊。

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
|*psaExtensionNames*|適用于 Office 的應用程式延伸模組名稱。|

## <a name="return-value"></a>傳回值
 HRESULT 值，表示此方法是否已順利完成。

## <a name="remarks"></a>備註
 要插入的每個 Office 應用程式都會以 Office 應用程式延伸模組名稱的形式傳回，該名稱會對應至 **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer** 下的值。 主機必須查閱登錄中的這些值，然後自動插入延伸模組。
