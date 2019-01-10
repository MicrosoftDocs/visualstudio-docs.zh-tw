---
title: 複製 （程式設計擷取） |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aab2b18c8c349211f4b5bd26b055d6ee5b65f0c6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990944"
---
# <a name="copy-programmatic-capture"></a>複製 (程式設計擷取)
使用中的圖形記錄 (.vsglog) 檔案的內容複製到新的檔案。  
  
## <a name="syntax"></a>語法  
  
```C++  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>參數  
 `szNewVSGLog`  
 新的圖形記錄檔的檔案名稱。  
  
## <a name="remarks"></a>備註  
 若要將圖形資訊複製到新的檔案中，您必須已經擷取某些圖形資訊;否則，會發生任何事。