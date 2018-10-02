---
title: 'Idiaaddressmap:: Put_addressmapenabled |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe8d1dcd58c745bdba44f1fa895ba87cb6a9b7f4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498407"
---
# <a name="idiaaddressmapputaddressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[idiaaddressmap:: Put_addressmapenabled](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled)。  
  
指定對應位址是否應該用來將符號位址轉譯。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 NewVal  
 [in]設定為`TRUE`啟用的符號，轉譯或`FALSE`停用。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 可執行的後置處理器有時會更新可執行檔。 DIA 包含支援新的版面配置將符號的轉譯機制。  
  
 載入 PDB 檔案時，就會儲存在檔案中的對應位址啟用。 有些的時候，不過，當用戶端應用程式可能需要提供自己的位址對應，藉由呼叫[idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)方法。 如果`set_addressMap`方法會成功，用戶端應用程式必須呼叫`put_addressMapEnabled`方法`NewVal`參數`TRUE`若要啟用的位址對應。  
  
 正在啟用的地址對應的目前狀態可以藉由呼叫擷取[idiaaddressmap:: Get_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)



