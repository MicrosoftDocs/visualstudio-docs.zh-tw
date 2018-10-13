---
title: UnInit |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 485a00c5e05b04873cfdcbf10c428786408e3a72
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298099"
---
# <a name="uninit"></a>UnInit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

完成的圖形記錄檔、 關閉，並釋出應用程式的作用中記錄的圖形資訊時所使用的資源。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void UnInit();  
```  
  
## <a name="remarks"></a>備註  
 `UnInit` 執行個體時自動呼叫`VsgDbg`終結類別之前。 如果`VsgDbg`執行個體所未主動記錄圖形資訊，這沒有任何作用。  
  
 之後`UnInit`的執行個體上呼叫`VsgDbg`類別，新的圖形記錄檔可由呼叫`Init`並完成藉由呼叫`UnInit`。 您可以重複此步驟為您想要使用相同的多次`VsgDbg`來建立數個獨立的圖形記錄檔的執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [Init](../debugger/init.md)



