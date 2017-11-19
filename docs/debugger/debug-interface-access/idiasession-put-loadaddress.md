---
title: "Idiasession:: Put_loadaddress |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b12ef6fa6da9338346aa997ba16cb023548f138
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
符號設定載入位址，對應的可執行檔，此符號存放區中。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `NewVal`  
 [in]載入的可執行檔的位址。  
  
## <a name="remarks"></a>備註  
 符號虛擬位址 (VA) 屬性會使用此方法的值來計算。 除非此屬性已設為非零，才會計算虛擬位址。  
  
> [!NOTE]
>  您必須先呼叫這個方法，當您取得[IDiaSession](../../debugger/debug-interface-access/idiasession.md)物件，並開始使用物件，如果您需要使用在符號上的任何虛擬屬性之前。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)