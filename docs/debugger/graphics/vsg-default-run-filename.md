---
description: 定義圖形記錄檔的預設檔案名稱。
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5f6bd07e54fc90bcc99f7462cc087ba01866727c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160476"
---
# <a name="vsg_default_run_filename"></a>VSG_DEFAULT_RUN_FILENAME
定義圖形記錄檔的預設檔案名稱。

## <a name="syntax"></a>語法

```C++
#define VSG_DEFAULT_FILENAME filename
```

#### <a name="parameters"></a>參數
 `filename` 當以程式設計方式捕捉圖形資訊時，預設會提供給圖形記錄檔的檔案名。

## <a name="value"></a>值
 表示圖形記錄檔檔案名的字串常值。 預設為 L "vsglog"。

```C++
#define VSG_DEFAULT_FILENAME L"default.vsglog"
```

## <a name="remarks"></a>備註
 如果已定義預處理器符號 `DONT_SAVE_VSGLOG_TO_TEMP` ，則檔案名會相對於所捕獲應用程式的目前的目錄，或者是絕對路徑; 否則，它會相對於使用者的暫存檔案目錄，而不能是絕對路徑。

 若要變更定義的檔案名，您必須在包含于程式之前重新定義該名稱 `vsgcapture.h` 。

## <a name="example"></a>範例
 此範例顯示如何變更 capture 檔案的預設檔案名：

```C++
// Redefine the default capture filename before including vsgcapture.h
#define VSG_DEFAULT_FILENAME L"capture.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>另請參閱
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
