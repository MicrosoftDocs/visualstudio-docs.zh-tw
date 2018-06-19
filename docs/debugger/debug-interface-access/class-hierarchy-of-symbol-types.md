---
title: 類別階層架構的符號類型 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa8aeb208c4015d205efbfe018ee324a8ba0ede6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468849"
---
# <a name="class-hierarchy-of-symbol-types"></a>符號類型的類別階層架構
下表描述在類別階層中的符號類型。  
  
## <a name="symbol-types"></a>符號類型  
  
|符號類型|描述|  
|-----------------|-----------------|  
|[UDT](../../debugger/debug-interface-access/udt.md)|用來代表每個類別、 結構和等位的符號。|  
|[Enum (偵錯介面存取 SDK)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|列舉類型的符號。|  
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|指標類型的符號。|  
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|陣列類型的符號。|  
|[BaseType](../../debugger/debug-interface-access/basetype.md)|基底類型的符號|  
|[Typedef (偵錯介面存取 SDK)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|導入了其他類型的名稱的符號。|  
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|使用者定義型別 (UDT) 的每個基底類別所使用的符號。|  
|[Friend (偵錯介面存取 SDK)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Friend 類別和 friend 函式符號。|  
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|每個唯一的函式簽章的符號。|  
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|針對每個函式的參數符號。|  
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|虛擬資料表大小的符號。|  
|[VTable](../../debugger/debug-interface-access/vtable.md)|一份虛擬資料表的符號。|  
|[CustomType](../../debugger/debug-interface-access/customtype.md)|廠商定義的類型的符號。|  
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|中繼資料中所定義之類型的符號。|  
|[維度](../../debugger/debug-interface-access/dimension.md)|陣列維度的符號。|  
  
> [!NOTE]
>  每個符號可以有保存相關的符號，以及其他符號的參考資訊的屬性。 在個別的符號主題中列出了這些屬性。  
  
## <a name="see-also"></a>另請參閱  
 [CV_access_e 列舉](../../debugger/debug-interface-access/cv-access-e.md)   
 [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [符號和符號標記](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)