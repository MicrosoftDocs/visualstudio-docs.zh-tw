---
title: 設定目前處理序 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5281d1c0d926d8d6acdedf323649216c74a4cab9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490113"
---
# <a name="set-current-process"></a>設定目前處理序
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[設定目前的處理序](https://docs.microsoft.com/visualstudio/ide/reference/set-current-process)。  
  
  
將指定的處理序設為偵錯工具中的使用中處理序。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.SetCurrentProcess index  
```  
  
## <a name="arguments"></a>引數  
 `index`  
 必要。 處理序的索引。  
  
## <a name="remarks"></a>備註  
 進行偵錯時，您可以附加至多個處理序，但是無論在任何時間，偵錯工具一次只能有一個使用中處理序。 您可以使用 `SetCurrentProcess` 命令設定使用中處理序。  
  
## <a name="example"></a>範例  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)



