---
title: "設定目前處理序 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eb673db29a4bb106aa4c9c4d9022293367e8ed4f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="set-current-process"></a>設定目前處理序
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
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)