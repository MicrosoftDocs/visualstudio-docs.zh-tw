---
title: "Idiadatasource:: Opensession |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6b7cfaf3e2cf7331576ca79b9820bafb761fc44c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
開啟查詢符號的工作階段。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>參數  
 ppSession  
 [out]傳回[IDiaSession](../../debugger/debug-interface-access/idiasession.md)物件，表示開啟的工作階段。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 下表顯示可能的傳回值，這個方法。  
  
|值|描述|  
|-----------|-----------------|  
|E_UNEXPECTED|[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)物件先前尚未初始化符號的來源。|  
|E_INVALIDARG|無效`ppSession`參數。|  
|E_OUTOFMEMORY|記憶體不足，無法開啟工作階段。|  
  
## <a name="remarks"></a>備註  
 這個方法會開啟[IDiaSession](../../debugger/debug-interface-access/idiasession.md)資料來源的物件。  
  
 `IDiaSession`物件會實作查詢到的資料來源。 工作階段會管理針對每個偵錯符號集的一個位址空間。 描述的資料來源符號的.exe 或.dll 檔案是否作用中多個位址範圍 （例如，因為多個處理序已經載入它），則應該用於每個位址範圍的一個工作階段。  
  
## <a name="example"></a>範例  
  
```C++  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [概觀](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [查詢 .Pdb 檔案](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)