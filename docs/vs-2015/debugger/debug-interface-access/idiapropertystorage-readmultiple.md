---
title: IDiaPropertyStorage::ReadMultiple |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c36dcd5fc0f6e02804c57d94c9ae1d5c05e3b19f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796229"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

讀取指定從目前的屬性集的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cpspec`  
 [in]屬性中指定的計數`rgpspec`陣列。 如果是零，此方法會傳回任何屬性，但傳回`S_OK`為成功的程式碼。  
  
 `rgpspec`  
 [in]要讀取的屬性陣列。 屬性可以指定屬性識別碼或選擇性的字串名稱。 您不需要指定屬性陣列中任何特定順序。 陣列可以包含重複的屬性，導致重複的屬性值在傳回簡單的屬性。 非簡單屬性應該傳回以開啟第二次嘗試存取被拒。 陣列可以包含混合的屬性識別碼和字串識別碼。 這個陣列至少必須有`cpspec`屬性值的數字。  
  
 `rgvar`  
 [in、 out]陣列`PROPVARIANT`結構 （在 Microsoft.VisualStudio.OLE.Interop 命名空間中），來填入每個屬性值。 此陣列必須至少是`cpspec`大小的項目。 呼叫端不需要初始化的陣列中的值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`。 傳回`S_FALSE`如果找不到一或多個屬性。 否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果屬性找不到，在對應的項目`rgvar`陣列包含`VARIANT`的型別`VT_EMPTY`。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)



