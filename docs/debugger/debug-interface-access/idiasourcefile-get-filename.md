---
title: IDiaSourceFile::get_fileName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_fileName method
ms.assetid: a5cb8927-23c6-469e-8f78-f2787d85dba4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35935f3f61fbbdc4ded91c7f1ec2f3d03e6cefab
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465290"
---
# <a name="idiasourcefileget_filename"></a>IDiaSourceFile::get_fileName
抓取來原始檔案名。

## <a name="syntax"></a>語法

```C++
HRESULT get_fileName ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回來原始檔案名。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)