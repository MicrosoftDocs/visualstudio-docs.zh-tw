---
title: 符號類型的類別階層 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839188"
---
# <a name="class-hierarchy-of-symbol-types"></a>符號類型的類別階層架構
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

下表描述類別階層架構中的符號類型。  
  
## <a name="symbol-types"></a>符號類型  
  
|符號類型|描述|  
|-----------------|-----------------|  
|[UDT](../../debugger/debug-interface-access/udt.md)|用來表示每個類別、結構和等位的符號。|  
|[Enum (偵錯介面存取 SDK)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|列舉類型的符號。|  
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|指標類型的符號。|  
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|陣列類型的符號。|  
|[BaseType](../../debugger/debug-interface-access/basetype.md)|基底類型的符號|  
|[Typedef (偵錯介面存取 SDK)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|引進其他類型名稱的符號。|  
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|使用者自訂類型的每個基類所使用的符號 (UDT) 。|  
|[Friend (偵錯介面存取 SDK)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Friend 類別和 friend 函數的符號。|  
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|每個唯一函數簽章的符號。|  
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|函數之每個參數的符號。|  
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|虛擬資料表大小的符號。|  
|[VTable](../../debugger/debug-interface-access/vtable.md)|虛擬資料表的符號。|  
|[CustomType](../../debugger/debug-interface-access/customtype.md)|廠商定義類型的符號。|  
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|中繼資料中定義之類型的符號。|  
|[維度](../../debugger/debug-interface-access/dimension.md)|陣列維度的符號。|  
  
> [!NOTE]
> 每個符號都可以有屬性（property），其中包含符號的相關資訊，以及其他符號的參考。 這些屬性會列在個別的符號主題中。  
  
## <a name="see-also"></a>另請參閱  
 [CV_access_e 列舉](../../debugger/debug-interface-access/cv-access-e.md)   
 [符號類型的詞法階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [符號和符號標記](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
