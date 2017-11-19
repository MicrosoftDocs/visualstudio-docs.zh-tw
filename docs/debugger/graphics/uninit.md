---
title: "UnInit |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 285cfb5a68055612fc7d77022b8f9d1d61067ded
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="uninit"></a>UnInit
終結的圖形記錄檔，就會關閉它，並釋出應用程式的作用中記錄的圖形資訊時所使用的資源。  
  
## <a name="syntax"></a>語法  
  
```C++  
void UnInit();  
```  
  
## <a name="remarks"></a>備註  
 `UnInit`執行個體時自動呼叫`VsgDbg`終結類別之前。 如果`VsgDbg`執行個體所未主動記錄圖形資訊，這會有任何作用。  
  
 之後`UnInit`的執行個體上呼叫`VsgDbg`類別，在新的圖形記錄檔可以藉由呼叫建立`Init`以及藉由呼叫進行最終處理`UnInit`。 您可以重複此步驟，您想要使用相同的次數`VsgDbg`建立數個獨立的圖形記錄檔的執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [Init](init.md)