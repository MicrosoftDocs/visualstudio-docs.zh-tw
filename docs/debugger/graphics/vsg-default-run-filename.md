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
ms.openlocfilehash: cb56f7ef08241aed2e109e6845af8fb596cb42e4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711822"
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
定義圖形記錄檔的預設檔案名稱。

## <a name="syntax"></a>語法

```C++
#define VSG_DEFAULT_FILENAME filename
```

#### <a name="parameters"></a>參數
 `filename` 當以程式設計方式擷取圖形資訊，指定預設圖形記錄檔的檔名。

## <a name="value"></a>值
 字串常值，表示檔案名稱的圖形記錄檔。 根據預設，L"default.vsglog"。

```C++
#define VSG_DEFAULT_FILENAME L"default.vsglog"
```

## <a name="remarks"></a>備註
 如果前置處理器符號`DONT_SAVE_VSGLOG_TO_TEMP`是定義，然後檔案名稱是相對於目前的目錄，擷取應用程式，或者是絕對路徑; 否則它是相對於使用者的 temporary files 目錄，不能是絕對路徑。

 若要變更定義的檔案名稱，您必須重新定義它後再納入`vsgcapture.h`在程式中。

## <a name="example"></a>範例
 此範例示範如何變更擷取檔案的預設檔案名稱：

```C++
// Redefine the default capture filename before including vsgcapture.h
#define VSG_DEFAULT_FILENAME L"capture.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>請參閱
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)