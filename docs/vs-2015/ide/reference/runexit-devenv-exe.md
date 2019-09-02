---
title: -Runexit (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- runexit Devenv switch
- Devenv, /runexit switch
- /runexit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0206f01df517c2dbd0c1c4052201dc8ded1bcbf9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163414"
---
# <a name="runexit-devenvexe"></a>/Runexit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

編譯並執行指定的專案或解決方案，然後關閉整合式開發環境 (IDE)。  
  
## <a name="syntax"></a>語法  
  
```  
devenv /runexit {SolutionName|ProjectName}  
```  
  
## <a name="arguments"></a>引數  
 `SolutionName`  
 必要項。 方案檔的完整路徑和名稱。  
  
 `ProjectName`  
 必要項。 專案檔的完整路徑和名稱。  
  
## <a name="remarks"></a>備註  
 根據為使用中方案組態所指定的設定，編譯並執行指定的專案或方案。 這個參數在專案或解決方案執行時會將 IDE 最小化，並在專案或解決方案完成執行之後關閉 IDE。  
  
- 請以雙引號括住包含空格的字串。  
  
- 摘要資訊 (包含錯誤) 可以顯示在 [命令]  視窗中，或使用 `/out` 參數指定的任何記錄檔中。  
  
## <a name="example"></a>範例  
 這個範例會在最小化的 IDE 中，以使用中部署設定來執行解決方案 `MySolution`，然後關閉 IDE。  
  
```  
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## <a name="see-also"></a>另請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)   
 [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
