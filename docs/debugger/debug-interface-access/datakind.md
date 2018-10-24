---
title: DataKind |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f2b46e420db8addf19ef8694112058bdb8b2f91
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867620"
---
# <a name="datakind"></a>DataKind
指出特定資料值的範圍。  
  
## <a name="syntax"></a>語法  
  
```C++  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## <a name="elements"></a>項目  
 DataIsUnknown  
 無法判斷資料符號。  
  
 DataIsLocal  
 資料項目是本機變數。  
  
 DataIsStaticLocal  
 資料項目是靜態區域變數。  
  
 DataIsParam  
 資料項目是型式參數。  
  
 DataIsObjectPtr  
 資料的項目就是物件指標 (`this`)。  
  
 DataIsFileStatic  
 資料的項目是檔案範圍的變數。  
  
 DataIsGlobal  
 資料項目是全域變數。  
  
 DataIsMember  
 資料項目是物件成員變數。  
  
 DataIsStaticMember  
 資料項目是類別的靜態變數。  
  
 DataIsConstant  
 資料項目是常數值。  
  
## <a name="remarks"></a>備註  
 傳回這個列舉型別中的值[idiasymbol:: Get_datakind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst.h  
  
## <a name="see-also"></a>另請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)