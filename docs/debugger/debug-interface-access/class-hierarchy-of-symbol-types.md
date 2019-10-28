---
title: 符號類型的類別階層 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c42ea4bb2d5c2ad91538bec8b31774a5a41aa4d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745449"
---
# <a name="class-hierarchy-of-symbol-types"></a>符號類型的類別階層架構
下表描述類別階層中的符號類型。

## <a name="symbol-types"></a>符號類型

|符號類型|描述|
|-----------------|-----------------|
|[UDT](../../debugger/debug-interface-access/udt.md)|用來代表每個類別、結構和聯集的符號。|
|[Enum (偵錯介面存取 SDK)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|列舉類型的符號。|
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|指標類型的符號。|
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|陣列類型的符號。|
|[BaseType](../../debugger/debug-interface-access/basetype.md)|基底類型的符號|
|[Typedef (偵錯介面存取 SDK)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|引進其他類型名稱的符號。|
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|用於使用者定義型別（UDT）之每個基類的符號。|
|[Friend (偵錯介面存取 SDK)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Friend 類別和 friend 函式的符號。|
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|每個唯一函數簽名的符號。|
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|函式的每個參數的符號。|
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|虛擬資料表大小的符號。|
|[VTable](../../debugger/debug-interface-access/vtable.md)|虛擬資料表的符號。|
|[CustomType](../../debugger/debug-interface-access/customtype.md)|廠商定義類型的符號。|
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|中繼資料中定義之類型的符號。|
|[維度](../../debugger/debug-interface-access/dimension.md)|陣列維度的符號。|

> [!NOTE]
> 每個符號都可以擁有保存符號相關資訊的屬性，以及其他符號的參考。 這些屬性會列在個別的符號主題中。

## <a name="see-also"></a>另請參閱
- [CV_access_e 列舉](../../debugger/debug-interface-access/cv-access-e.md)
- [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [符號和符號標記](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)