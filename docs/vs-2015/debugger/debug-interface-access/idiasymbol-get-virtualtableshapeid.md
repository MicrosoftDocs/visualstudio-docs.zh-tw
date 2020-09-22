---
title: IDiaSymbol::get_virtualTableShapeId | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualTableShapeId method
ms.assetid: cbee9944-817a-4805-9c08-fac8e0da58b7
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e8b39aac8828efabee9057a417d6a9af50d959fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838941"
---
# <a name="idiasymbolget_virtualtableshapeid"></a>IDiaSymbol::get_virtualTableShapeId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取符號的虛擬資料表圖形符號識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_virtualTableShapeId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展傳回符號的虛擬資料表圖形符號 ID。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
 識別碼是 DIA SDK 所建立的唯一值，會將所有符號標示為唯一的。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
