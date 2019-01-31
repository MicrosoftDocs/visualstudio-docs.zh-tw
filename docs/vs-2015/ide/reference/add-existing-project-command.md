---
title: 加入現有專案命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7523db6598a32c76944c22bfdabe56ee288c6b43
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771078"
---
# <a name="add-existing-project-command"></a>加入現有專案命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
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
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
