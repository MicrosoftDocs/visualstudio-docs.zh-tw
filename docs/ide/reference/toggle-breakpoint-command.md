---
title: 切換中斷點命令 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8ddbcf2cb47c5e83f2ce23833e3a206b7aaf7fe4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="toggle-breakpoint-command"></a>切換中斷點命令
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
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)