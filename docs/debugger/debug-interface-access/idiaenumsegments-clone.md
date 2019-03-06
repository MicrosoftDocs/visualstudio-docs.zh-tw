---
title: IDiaEnumSegments::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Clone method
ms.assetid: 93deaac6-72ab-4408-ba14-66174a618757
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9992b17155601284387981a9b424a77d3d9b5580
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616608"
---
# <a name="idiaenumsegmentsclone"></a>IDiaEnumSegments::Clone
建立列舉值，包含目前的列舉值相同的列舉型別狀態。

## <a name="syntax"></a>語法

```C++
HRESULT Clone ( 
   IDiaEnumSegments** ppenum
);
```

#### <a name="parameters"></a>參數
 ppenum

[out]傳回[IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)物件，包含列舉值重複。 不重複的區段，將列舉值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)