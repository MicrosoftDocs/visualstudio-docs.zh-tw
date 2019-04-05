---
title: IDiaSession::put_loadAddress | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1be0bfd6d5a635dcff632e25421922697b3f0de6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944720"
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

符號設定對應的可執行檔載入位址，此符號存放區中。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `NewVal`  
 [in]載入的可執行檔的位址。  
  
## <a name="remarks"></a>備註  
 符號虛擬位址 (VA) 屬性會使用此方法的值來計算。 除非此屬性將設為非零，才會計算虛擬位址。  
  
> [!NOTE]
>  您必須先呼叫這個方法，當您取得[IDiaSession](../../debugger/debug-interface-access/idiasession.md)物件，並開始使用的物件，如果您需要使用任何虛擬屬性上符號之前。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
