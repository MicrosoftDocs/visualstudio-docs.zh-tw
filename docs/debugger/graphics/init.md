---
title: Init |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0436384e0af816475590ab84dc645848113f5ab7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476194"
---
# <a name="init"></a>Init
準備主動擷取和記錄到圖形記錄檔的圖形資訊的圖形診斷的應用程式元件。  
  
## <a name="syntax"></a>語法  
  
```C++  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### <a name="parameters"></a>參數  
 `vsgLogGetter`  
 可呼叫的實體，例如函式、 函式指標、 lambda 或函式物件 — 會做為參數組成緩衝區的長度`wchar_t`和一個指標，該緩衝區，並傳回`void`。 叫用時，可呼叫的實體可決定將用來記錄圖形的詳細資訊，並將它寫入至指定的緩衝區中，傳回之前的檔案名稱。  
  
## <a name="remarks"></a>備註  
 `Init`的執行個體時自動呼叫函式`VsgDbg`類別建構，藉由指定`bDefaultInit`做為其建構函式參數`true`，否則`Init`之前您必須明確地呼叫可以主動擷取及記錄的圖形資訊。  
  
 您可以完成並關閉使用中的圖形記錄檔藉由呼叫`UnInit`，然後擷取並錄製新的圖形記錄檔的多個圖形資訊，藉由呼叫`Init`一次。 您可以依您想要建立數個獨立的圖形記錄檔使用相同的次數重複這`VsgDbg`執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [UnInit](init.md)