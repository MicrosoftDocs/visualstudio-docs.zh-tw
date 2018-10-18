---
title: Init |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a630906fa2a23a87853e8a835f155cda3ec06ecc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252391"
---
# <a name="init"></a>Init
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

準備圖形診斷，以主動擷取和記錄到圖形記錄檔的圖形資訊的應用程式元件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### <a name="parameters"></a>參數  
 `vsgLogGetter`  
 可呼叫的實體，例如函式、 函式指標，lambda 或函式物件，會做為參數所組成的緩衝區長度`wchar_t`以及該緩衝區，並傳回的指標`void`。 叫用時，可呼叫的實體可決定將用來記錄圖形的詳細資訊，並將它寫入指定的緩衝區，再傳回的檔案名稱。  
  
## <a name="remarks"></a>備註  
 `Init`執行個體時自動呼叫函式`VsgDbg`類別的建構方式指定`bDefaultInit`做為其建構函式參數`true`; 否則即為`Init`之前您必須先明確地呼叫可以主動擷取並記錄圖形資訊。  
  
 您可以完成並關閉使用中的圖形記錄檔藉由呼叫`UnInit`，然後再擷取和記錄新的圖形記錄檔的多個圖形資訊，藉由呼叫`Init`一次。 您可以重複此步驟為您想要建立使用相同的數個獨立的圖形記錄檔的多次`VsgDbg`執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [UnInit](../debugger/init.md)



