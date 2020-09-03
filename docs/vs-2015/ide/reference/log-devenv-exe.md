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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f427edfe294605b7b2adcbb0889e48c4f37b6ba9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666837"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

將所有活動記錄至記錄檔中，以進行疑難排解。 在您至少呼叫 `devenv /log` 一次之後這個檔案才會出現。 根據預設，此記錄檔為：

 *%APPDATA%* \Microsoft\VisualStudio\\<版本>** \ActivityLog.xml

 其中 <版本>** 是 Visual Studio 版本。 不過，您可以指定不同的路徑和檔案名稱。

## <a name="syntax"></a>語法

```
Devenv /log Path\NameOfLogFile
```

## <a name="remarks"></a>備註
 這個參數必須出現在命令列結尾，位於所有其他參數之後。

 只要是您使用 /log 參數叫用的所有 Visual Studio 執行個體，都會為其寫入記錄。 但不會記錄沒有使用此參數所叫用的 Visual Studio 執行個體。

## <a name="see-also"></a>另請參閱
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
