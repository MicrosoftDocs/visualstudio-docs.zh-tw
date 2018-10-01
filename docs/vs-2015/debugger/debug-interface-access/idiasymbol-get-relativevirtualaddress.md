---
title: 'Idiasymbol:: Get_relativevirtualaddress |Microsoft Docs'
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
- IDiaSymbol::get_relativeVirtualAddress method
ms.assetid: e37219e3-c021-4057-9ec8-4f7cf3c13a15
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37cc20bf64ab13676dc40fdcbf3230192ebc9358
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496431"
---
# <a name="idiasymbolgetrelativevirtualaddress"></a>IDiaSymbol::get_relativeVirtualAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[idiasymbol:: Get_relativevirtualaddress](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress)。  
  
擷取位置的相對虛擬位址 (RVA)。 使用時機[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)設定為`LocIsStatic`。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_relativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回位置的相對虛擬位址。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。  
  
## <a name="example"></a>範例  
  
```cpp#  
IDiaSymbol* pSymbol;  
DWORD       rva;  
pSymbol->get_relativeVirtualAddress( &rva );  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)



