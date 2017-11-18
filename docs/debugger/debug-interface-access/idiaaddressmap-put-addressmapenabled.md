---
title: "Idiaaddressmap:: Put_addressmapenabled |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5542e00511301a84ba54a08405434001f63c4b5d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiaaddressmapputaddressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
指定是否會用於將符號位址轉譯對應位址。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 NewVal  
 [in]設定為`TRUE`啟用的符號，轉譯或`FALSE`停用。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 可執行檔後處理器有時會更新可執行檔。 DIA 包含以支援新的版面配置的符號的轉譯機制。  
  
 載入 PDB 檔案時，會啟用儲存在檔案中的位址對應。 有時候，不過，當用戶端應用程式可能需要提供自己的位址對應，藉由呼叫[idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)方法。 如果`set_addressMap`方法成功，用戶端應用程式必須呼叫`put_addressMapEnabled`方法`NewVal`參數`TRUE`來啟用的位址對應。  
  
 正在啟用的位址對應的目前狀態可擷取呼叫[idiaaddressmap:: Get_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)