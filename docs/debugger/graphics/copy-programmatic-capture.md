---
title: 複製 (程式設計捕獲) |Microsoft Docs
description: 您可以使用 VsgDbg 類別的 Copy 方法，將現用圖形記錄檔的內容複寫 (. vsglog) 檔案複製到新檔案中。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 62140f279d805e5162661c22110671871afff1ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879185"
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