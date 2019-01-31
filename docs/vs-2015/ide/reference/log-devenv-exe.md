---
title: -Log (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8e9e5178be0301bcf2ab14b0d52d6aa3b54bc52a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54763167"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
將所有活動記錄至記錄檔中，以進行疑難排解。 在您至少呼叫 `devenv /log` 一次之後這個檔案才會出現。 根據預設，此記錄檔為：  
  
 *%APPDATA%* \Microsoft\VisualStudio\\<版本>\ActivityLog.xml  
  
 其中 <版本> 是 Visual Studio 版本。 不過，您可以指定不同的路徑和檔案名稱。  
  
## <a name="syntax"></a>語法  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## <a name="remarks"></a>備註  
 這個參數必須出現在命令列結尾，位於所有其他參數之後。  
  
 只要是您使用 /log 參數叫用的所有 Visual Studio 執行個體，都會為其寫入記錄。 但不會記錄沒有使用此參數所叫用的 Visual Studio 執行個體。  
  
## <a name="see-also"></a>請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
