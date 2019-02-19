---
title: -DebugExe (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1edbcddd27f2c3637e0e56dd9b4841e17ace16af
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54767559"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
開啟要偵錯的指定可執行檔。  
  
## <a name="syntax"></a>語法  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## <a name="arguments"></a>引數  
 `ExecutableFile`  
 必要項。 .exe 檔案的路徑和檔案名稱。  
  
 如果 .exe 檔案找不到或不存在，則不會顯示任何警告或錯誤，而且 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 會正常啟動。  
  
## <a name="remarks"></a>備註  
 `ExecutableFile` 參數後面的任何字串都會當成引數傳遞給該檔案。  
  
## <a name="example"></a>範例  
 下列範例會開啟 `MyApplication.exe` 檔案以進行偵錯。  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## <a name="see-also"></a>請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
