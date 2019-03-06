---
title: SetThreadCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 656e491e683c7ec2de23ea7e49938e833af3a295
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709612"
---
# <a name="setthreadcount"></a>SetThreadCount
設定全域執行緒計數，並將該計數指派給目前的執行緒。

## <a name="syntax"></a>語法

```cmd
HRESULT WINAPI SetThreadCount(int threadCount);
```

#### <a name="parameters"></a>參數
[in] `threadCount`

 要使用的執行緒數目。

## <a name="return-value"></a>傳回值
 如已更新執行緒計數，則為 **HRESULT** 和已設定的 **SUCCEEDED** 位元。

## <a name="requirements"></a>需求
 **標頭：***FileTracker.h*