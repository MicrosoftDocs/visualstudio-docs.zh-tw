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
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736083"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
出現時，定義圖形記錄檔是否儲存到使用者的暫存檔目錄。

## <a name="syntax"></a>語法

```C++
#define DONT_SAVE_VSGLOG_TO_TEMP
```

## <a name="value"></a>值
 依其存在與否的預處理器符號會決定圖形記錄檔是否儲存至使用者的暫存檔案目錄。 如果已定義此符號，則 `VSG_DEFAULT_RUN_FILENAME` 所定義的檔案名會相對於所捕獲應用程式的目前目錄，或為絕對路徑;否則，`VSG_DEFAULT_RUN_FILENAME` 所定義的檔案名會相對於使用者的暫存檔案目錄，而且不能是絕對路徑。

## <a name="remarks"></a>備註
 視使用者的許可權而定，圖形記錄檔可能無法儲存在任意位置。 如果您不確定您選擇的位置是否可以由使用者寫入，建議您偏好將圖形記錄儲存到使用者的暫存檔案目錄或其他已知的位置。

 若要防止圖形記錄檔儲存到暫存檔案目錄，您必須先定義 `DONT_SAVE_VSGLOG_TO_TEMP`，才能包含 `vsgcapture.h`。

## <a name="example"></a>範例
 這個範例示範如何將圖形記錄檔儲存到主機電腦上的絕對路徑。

```cpp
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h
#define DONT_SAVE_VSGLOG_TO_TEMP
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>請參閱
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
