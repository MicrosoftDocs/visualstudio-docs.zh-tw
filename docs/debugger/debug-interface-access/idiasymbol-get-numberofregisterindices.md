---
title: "IDiaSymbol::get_numberOfRegisterIndices |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 1ec8b8ea-e423-4327-8dc0-a390e6e3ffb0
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d65c7d052e060cfca7f271fdc89014174055b02
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetnumberofregisterindices"></a>IDiaSymbol::get_numberOfRegisterIndices
擷取註冊索引鍵的數目。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_numberOfRegisterIndices(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]指標`DWORD`保存暫存索引鍵的數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)