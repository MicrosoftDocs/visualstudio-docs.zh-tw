---
title: 'Idiadatasource:: Opensession |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bea16f7ff0f723979ded9962a8ff9e620227f8ea
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53843108"
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
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。 下表顯示可能的傳回值，這個方法。  
  
|值|說明|  
|-----------|-----------------|  
|E_UNEXPECTED|[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)物件先前尚未初始化符號的來源。|  
|E_INVALIDARG|無效的 `ppSession` 參數。|  
|E_OUTOFMEMORY|若要開啟 工作階段的記憶體不足。|  
  
## <a name="remarks"></a>備註  
 這個方法會開啟[IDiaSession](../../debugger/debug-interface-access/idiasession.md)資料來源的物件。  
  
 `IDiaSession` 物件會實作到資料來源的查詢。 工作階段會管理每一組偵錯符號的一個位址空間。 資料來源符號所描述的.exe 或.dll 檔案是否作用中多個位址範圍 （例如，因為多個處理序已經載入它），則應該使用每個位址範圍的一個工作階段。  
  
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