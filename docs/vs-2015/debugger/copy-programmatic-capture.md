---
title: 複製 (程式設計捕獲) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa79ffc2081ba92b905838658fe6aa758a675192
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161505"
---
# <a name="copy-programmatic-capture"></a>複製 (程式設計擷取)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

將現用圖形記錄檔 ( 的內容複寫到新的檔案中。 vsglog) 檔案。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>參數  
 `szNewVSGLog`  
 新圖形記錄檔的檔案名。  
  
## <a name="remarks"></a>備註  
 若要將圖形資訊複製到新檔案，您必須已捕捉部分圖形資訊;否則，就不會發生任何事。
