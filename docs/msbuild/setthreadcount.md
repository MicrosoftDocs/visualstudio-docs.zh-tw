---
title: SetThreadCount | Microsoft Docs
description: 瞭解 MSBuild 如何使用 SetThreadCount 來設定全域執行緒計數，並將該計數指派給目前的執行緒。
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f7282b8c4589007492e48994628910b3a4ef0691
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966158"
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

## <a name="requirements"></a>規格需求

 **標頭：** *FileTracker.h*