---
title: 'Idiasession:: Put_loadaddress |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b0b04db800e5b61ef1598fe4c81a9ab362e375e3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31462642"
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