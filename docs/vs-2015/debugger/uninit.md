---
title: UnInit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0bec86a7f872057b7a0d652df6346e3a1ef2ff8a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197941"
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
