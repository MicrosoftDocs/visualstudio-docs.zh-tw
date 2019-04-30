---
title: 類別階層的符號類型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3a7b3edb0262e3e2b4f0cde51b499e25b04aba51
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442902"
---
# <a name="class-hierarchy-of-symbol-types"></a>符號類型的類別階層架構
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

下表描述的類別階層架構中的符號類型。  
  
## <a name="symbol-types"></a>符號類型  
  
|符號類型|描述|  
|-----------------|-----------------|  
|[UDT](../../debugger/debug-interface-access/udt.md)|用來代表每個類別、 結構和等位的符號。|  
|[Enum (偵錯介面存取 SDK)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|列舉類型的符號。|  
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|指標類型的符號。|  
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|陣列類型的符號。|  
|[BaseType](../../debugger/debug-interface-access/basetype.md)|針對基底類型的符號|  
|[Typedef (偵錯介面存取 SDK)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|導入其他類型的名稱的符號。|  
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|使用者定義型別 (UDT) 的每個基底類別所使用的符號。|  
|[Friend (偵錯介面存取 SDK)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Friend 類別和 friend 函式的符號。|  
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|每個唯一的函式簽章的符號。|  
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|每個參數的函式的符號。|  
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|符號的虛擬資料表大小。|  
|[VTable](../../debugger/debug-interface-access/vtable.md)|符號的虛擬資料表。|  
|[CustomType](../../debugger/debug-interface-access/customtype.md)|廠商定義的類型的符號。|  
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|型別的中繼資料中定義的符號。|  
|[維度](../../debugger/debug-interface-access/dimension.md)|陣列維度的符號。|  
  
> [!NOTE]
> 每個符號可以有屬性，保存相關的符號，以及其他符號的參考資訊。 在個別的符號主題中列出了這些屬性。  
  
## <a name="see-also"></a>另請參閱  
 [CV_access_e 列舉](../../debugger/debug-interface-access/cv-access-e.md)   
 [符號類型的語彙階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [符號和符號標記](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
