---
title: 'Idiastackwalkhelper:: Imageforva |Microsoft Docs'
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
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c386591172867f85b127c4744055e4c2bc37b5d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916162"
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

傳回在指定的虛擬位址某處可執行檔的記憶體空間中的記憶體中的可執行檔映像。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT imageForVA(  
   ULONGLONG  vaContext,  
   ULONGLONG *pvaImageStart  
);  
```  
  
#### <a name="parameters"></a>參數  
 `vaContext`  
 [in]介於兩者可執行檔的空間中的虛擬位址。  
  
 `pvaImageStart`  
 [out]傳回可執行檔的映像的起始虛擬位址。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)



