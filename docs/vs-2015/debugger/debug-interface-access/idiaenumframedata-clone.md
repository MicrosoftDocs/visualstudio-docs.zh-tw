---
title: 'Idiaenumframedata:: Clone |Microsoft Docs'
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
- IDiaEnumFrameData::Clone Method
ms.assetid: 28a17300-1626-422f-a17a-3a4d3872c37c
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9b658e0cf6d2d92df19d57051611e0ebb86663a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47484814"
---
# <a name="idiaenumframedataclone"></a>IDiaEnumFrameData::Clone
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[idiaenumframedata:: Clone](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumframedata-clone)。  
  
建立列舉值，包含目前的列舉值相同的列舉型別狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Clone(   
   IDiaEnumFrameData** ppenum  
);  
```  
  
#### <a name="parameters"></a>參數  
 ppenum  
 [out]傳回[IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)物件，包含列舉值重複。 框架資料不被重複的列舉值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)



