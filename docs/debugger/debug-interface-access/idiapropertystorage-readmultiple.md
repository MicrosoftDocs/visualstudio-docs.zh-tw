---
title: IDiaPropertyStorage::ReadMultiple |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cd1cb40554409fc534f0f13033dca499095d0b51
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
讀取指定從目前的屬性集的屬性。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cpspec`  
 [in]屬性中指定的計數`rgpspec`陣列。 如果是零，方法會傳回任何屬性，但傳回`S_OK`為成功的程式碼。  
  
 `rgpspec`  
 [in]要讀取的屬性陣列。 屬性可以指定屬性識別碼或選擇性字串名稱。 您不需要指定屬性陣列中任何特定順序。 陣列可以包含重複的屬性，產生重複的屬性值傳回簡單的屬性。 非簡單內容應該傳回以開啟第二次嘗試存取被拒。 陣列可以包含混合的屬性識別碼與字串識別碼。 這個陣列至少必須有`cpspec`屬性值的數字。  
  
 `rgvar`  
 [in、 out]陣列`PROPVARIANT`結構 （在 Microsoft.VisualStudio.OLE.Interop 命名空間中），以填入每個屬性值。 陣列必須至少`cpspec`中大小的項目。 呼叫端不需要初始化陣列中的值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`。 傳回`S_FALSE`如果找不到一或多個屬性。 否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果不找到屬性，對應的項目中`rgvar`陣列包含`VARIANT`的型別`VT_EMPTY`。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)