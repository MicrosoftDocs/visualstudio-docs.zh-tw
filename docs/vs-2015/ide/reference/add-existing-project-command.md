---
title: 加入現有專案命令 | Microsoft Docs
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
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 048ba8e43b66ac5ad4bbc1d0c09adb75a2d61e1d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485795"
---
# <a name="add-existing-project-command"></a>加入現有專案命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[加入現有專案命令](https://docs.microsoft.com/visualstudio/ide/reference/add-existing-project-command)。  
  
  
將現有專案新增至目前的方案。  
  
## <a name="syntax"></a>語法  
  
```  
File.AddExistingProject filename  
```  
  
## <a name="arguments"></a>引數  
 `filename`  
 選擇性。 要新增至方案的專案完整路徑和專案名稱，包括副檔名。  
  
 如果 `filename` 引數包含空格，必須以引號括住。  
  
 如果未指定任何檔名，此命令將會開啟 [檔案] 對話方塊，以供使用者選取專案。  
  
## <a name="remarks"></a>備註  
 自動完成會在您輸入時嘗試找出正確的路徑和檔名。  
  
## <a name="example"></a>範例  
 此範例會將 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 專案 TestProject1 新增至目前的方案。  
  
```  
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)



