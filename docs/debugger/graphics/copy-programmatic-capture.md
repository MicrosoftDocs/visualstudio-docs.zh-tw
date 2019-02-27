---
title: 複製 （程式設計擷取） |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a888605cfae6b5430782defd198f83988c31870
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719076"
---
# <a name="copy-programmatic-capture"></a>複製 (程式設計擷取)
使用中的圖形記錄 (.vsglog) 檔案的內容複製到新的檔案。

## <a name="syntax"></a>語法

```C++
void Copy(
  wchar_t const * szNewVSGLog
);
```

#### <a name="parameters"></a>參數
 `szNewVSGLog` 新的圖形記錄檔的檔案名稱。

## <a name="remarks"></a>備註
 若要將圖形資訊複製到新的檔案中，您必須已經擷取某些圖形資訊;否則，會發生任何事。