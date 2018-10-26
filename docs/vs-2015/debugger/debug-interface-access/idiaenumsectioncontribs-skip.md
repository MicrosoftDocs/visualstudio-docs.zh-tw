---
title: 'Idiaenumsectioncontribs:: Skip |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaEnumSectionContribs::Skip method
ms.assetid: 7471a178-5134-41b2-80a6-51ff96abe916
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d79f7b097bafab887fc200f2c0c1aa2f4aebd0ce
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935018"
---
# <a name="idiaenumsectioncontribsskip"></a>IDiaEnumSectionContribs::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

略過指定的數目的列舉型別序列中的區段比重。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Skip(   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in]略過列舉序列中的區段貢獻數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`是否略過任何更多區段投稿內容。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)



