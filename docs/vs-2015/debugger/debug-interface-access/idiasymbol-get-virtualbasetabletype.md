---
title: IDiaSymbol::get_virtualBaseTableType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ea59822ebc568e843433f28f6e9b23f4df96fdb2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838920"
---
# <a name="idiasymbolget_virtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取虛擬基底資料表指標的類型。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_virtualBaseTableType(  
   IDiaSymbol *pRetVal  
};  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`pRetVal`|擴展傳回 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件，這個物件會指定基表的型別。|  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。  
  
## <a name="remarks"></a>備註  
 虛擬基底資料表指標 (`vbtptr`) 是 vtable 中的隱藏指標 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] ，可處理來自虛擬基類的繼承。 `vbtptr`根據繼承的類別，可以有不同的大小。  
  
 這個方法會傳回 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件，可用來判斷 vbtptr 的大小。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2。h|  
|版本：|DIA SDK v8.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
