---
title: 複製 （程式設計擷取） |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: 171dd04a4f2c933272a7addc787554f611b1449f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491928"
---
# <a name="copy-programmatic-capture"></a>複製 (程式設計擷取)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[複製 （程式設計擷取）](https://docs.microsoft.com/visualstudio/debugger/graphics/copy-programmatic-capture)。  
  
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



