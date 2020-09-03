---
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40f3c3c22de6b4b0ebdbdf2dfc953f4cb1c9b5e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72736083"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
出現時，定義圖形記錄檔是否儲存到使用者的暫存檔目錄。

## <a name="syntax"></a>語法

```C++
#define DONT_SAVE_VSGLOG_TO_TEMP
```

## <a name="value"></a>值
 以其目前狀態或缺席為依據的預處理器符號，決定圖形記錄檔是否儲存至使用者的暫存檔案目錄。 如果已定義此符號，則由所定義的檔案名 `VSG_DEFAULT_RUN_FILENAME` 會相對於所捕捉應用程式的目前的目錄，或者是絕對路徑; 否則，所定義的檔案名 `VSG_DEFAULT_RUN_FILENAME` 會相對於使用者的暫存檔案目錄，而不能是絕對路徑。

## <a name="remarks"></a>備註
 根據使用者的許可權，圖形記錄檔可能無法儲存在任意位置。 如果您不確定使用者是否可寫入您所選擇的位置，建議您最好將圖形記錄儲存到使用者的 [暫存檔案] 目錄或另一個已知良好的位置。

 為了避免將圖形記錄檔儲存至暫存檔案目錄，您必須在 `DONT_SAVE_VSGLOG_TO_TEMP` 包含之前先定義 `vsgcapture.h` 。

## <a name="example"></a>範例
 此範例示範如何將圖形記錄檔儲存至主機電腦上的絕對路徑。

```cpp
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h
#define DONT_SAVE_VSGLOG_TO_TEMP
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>另請參閱
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
