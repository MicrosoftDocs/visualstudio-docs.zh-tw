---
title: GetVstoSolutionMetadata 函式
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
ms.openlocfilehash: aebbedaab7e7ac342f6d6ace191d820f6a0c8090
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520181"
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

|參數|說明|
|---------------|-----------------|
|*lpwszSolutionMetadataKey*|請勿使用。|
|*ppSolutionInfo*|請勿使用。|

## <a name="return-value"></a>傳回值
 如果函式成功，它會傳回 **S_OK**。 如果函式失敗，則會傳回錯誤碼。
