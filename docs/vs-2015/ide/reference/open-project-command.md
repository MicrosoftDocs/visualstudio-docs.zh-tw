---
title: 開啟專案命令 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c8f70d5605f4ee47171992e3a94c145cbdc8785
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485101"
---
# <a name="open-project-command"></a>開啟專案命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[開啟 [專案] 命令](https://docs.microsoft.com/visualstudio/ide/reference/open-project-command)。  
  
  
開啟現有專案。  
  
## <a name="syntax"></a>語法  
  
```  
File.OpenProject filename  
```  
  
## <a name="arguments"></a>引數  
 `filename`  
 必要。 要開啟之專案的完整路徑和檔案名稱。  
  
 `filename` 引數的語法需要包含空格的路徑使用引號。  
  
## <a name="remarks"></a>備註  
 自動完成會在您輸入時嘗試找出正確的路徑和檔名。  
  
 偵錯時，無法使用此命令。  
  
## <a name="example"></a>範例  
 此範例會開啟 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 專案 Test1。  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)



