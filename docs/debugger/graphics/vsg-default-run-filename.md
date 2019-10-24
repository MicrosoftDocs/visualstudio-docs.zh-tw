---
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 835e2cec19e36418091e094abd2ec76bd6403398
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734834"
---
# <a name="vsg_default_run_filename"></a>VSG_DEFAULT_RUN_FILENAME
定義圖形記錄檔的預設檔案名稱。

## <a name="syntax"></a>語法

```C++
#define VSG_DEFAULT_FILENAME filename
```

#### <a name="parameters"></a>參數
 當以程式設計方式捕捉圖形資訊時，`filename` 預設提供給圖形記錄檔的檔案名。

## <a name="value"></a>值
 字串常值，表示圖形記錄檔的檔案名。 預設值為 L "default. vsglog"。

```C++
#define VSG_DEFAULT_FILENAME L"default.vsglog"
```

## <a name="remarks"></a>備註
 如果已定義預處理器符號 `DONT_SAVE_VSGLOG_TO_TEMP`，則檔案名會相對於所捕獲應用程式的目前目錄，或是絕對路徑;否則，它會相對於使用者的暫存檔案目錄，而且不能是絕對路徑。

 若要變更定義的檔案名，您必須重新定義它，才能在程式中包含 `vsgcapture.h`。

## <a name="example"></a>範例
 這個範例顯示如何變更 capture 檔案的預設檔案名：

```C++
// Redefine the default capture filename before including vsgcapture.h
#define VSG_DEFAULT_FILENAME L"capture.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>請參閱
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)