---
title: 複製 (程式設計捕獲) |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a888605cfae6b5430782defd198f83988c31870
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62895950"
---
# <a name="copy-programmatic-capture"></a>複製 (程式設計擷取)
將現用圖形記錄檔 ( 的內容複寫到新的檔案中。 vsglog) 檔案。

## <a name="syntax"></a>語法

```C++
void Copy(
  wchar_t const * szNewVSGLog
);
```

#### <a name="parameters"></a>參數
 `szNewVSGLog` 新圖形記錄檔的檔案名。

## <a name="remarks"></a>備註
 若要將圖形資訊複製到新檔案，您必須已捕捉部分圖形資訊;否則，就不會發生任何事。