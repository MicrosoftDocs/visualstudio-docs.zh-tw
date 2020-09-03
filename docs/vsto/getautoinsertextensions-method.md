---
title: GetAutoInsertExtensions 方法
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
ms.openlocfilehash: f5d88af6f24306b7b243359c9797a2cb7e7449bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543503"
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
 要插入的每個 Office 應用程式都會以 Office 應用程式延伸模組名稱的形式傳回，該名稱會對應至 **HKEY_CURRENT_USER \software\microsoft\office\wef\developer**下的值。 主機必須查閱登錄中的這些值，然後自動插入延伸模組。
