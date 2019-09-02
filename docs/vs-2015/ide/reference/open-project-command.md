---
title: 開啟專案命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: e2e945eb2faa492f576a0fd0a15fc0bd0e9b208e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199031"
---
# <a name="open-project-command"></a>開啟專案命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

開啟現有專案。  
  
## <a name="syntax"></a>語法  
  
```  
File.OpenProject filename  
```  
  
## <a name="arguments"></a>引數  
 `filename`  
 必要項。 要開啟之專案的完整路徑和檔案名稱。  
  
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
