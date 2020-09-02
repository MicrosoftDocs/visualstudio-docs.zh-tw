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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197941"
---
# <a name="uninit"></a>UnInit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

完成圖形記錄檔、將其關閉，並釋放應用程式主動記錄圖形資訊時所使用的資源。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void UnInit();  
```  
  
## <a name="remarks"></a>備註  
 `UnInit` 當終結類別的實例時，會自動呼叫 `VsgDbg` 。 如果 `VsgDbg` 實例未主動記錄圖形資訊，則不會有任何作用。  
  
 在 `UnInit` 類別的實例上呼叫之後，您 `VsgDbg` 可以藉由呼叫來建立新的圖形記錄檔， `Init` 並藉由呼叫來完成 `UnInit` 。 您可以重複這個動作，因為您想要使用相同的 `VsgDbg` 實例來建立數個獨立的圖形記錄檔。  
  
## <a name="see-also"></a>另請參閱  
 [Init](../debugger/init.md)
