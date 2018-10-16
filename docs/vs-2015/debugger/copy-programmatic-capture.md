---
title: 複製 （程式設計擷取） |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ec5c95a2419e465f93f7d11045672de2f1b0174
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49293185"
---
# <a name="copy-programmatic-capture"></a>複製 (程式設計擷取)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用中的圖形記錄 (.vsglog) 檔案的內容複製到新的檔案。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>參數  
 `szNewVSGLog`  
 新的圖形記錄檔的檔案名稱。  
  
## <a name="remarks"></a>備註  
 若要將圖形資訊複製到新的檔案中，您必須已經擷取某些圖形資訊;否則，會發生任何事。



