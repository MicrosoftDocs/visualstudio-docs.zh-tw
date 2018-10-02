---
title: 切換中斷點命令 | Microsoft Docs
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
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c7dd3bd7a4d42b8135aed034464223af53091f87
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485100"
---
# <a name="toggle-breakpoint-command"></a>切換中斷點命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[切換中斷點命令](https://docs.microsoft.com/visualstudio/ide/reference/toggle-breakpoint-command)。  
  
  
根據中斷點目前的狀態以及在檔案中的目前位置，將其開啟或關閉。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## <a name="arguments"></a>引數  
 `text`  
 選擇性。 如果指定文字，則會將行標示為具名中斷點。 否則，行會標示為未命名中斷點，其與按 F9 時所發生的作業類似。  
  
## <a name="example"></a>範例  
 下列範例會切換目前中斷點。  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)



