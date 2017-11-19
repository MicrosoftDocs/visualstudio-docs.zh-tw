---
title: "Idiaaddressmap:: Put_imagealign |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38856520641ff2ea191e3f712a1f355e841e1aff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
設定影像的對齊方式。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 NewVal  
 [in]新影像對齊值的可執行檔。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 指定的記憶體界限對齊映像 （載入可執行檔）。 此連接可以受到目前的系統架構和編譯和連結時間選項影響。 影像對齊方式一律為位元組界限上。 下列影像對齊是有效值： 1、 2、 4、 8、 16、 32 和 64 位元組界限。  
  
 可以藉由呼叫擷取目前的影像對齊[idiaaddressmap:: Get_imagealign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)方法。  
  
> [!NOTE]
>  可以呼叫這個方法已載入影像。 `put_imageAlign`映像已移動或變更和新的對齊是必要時，通常會使用方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)