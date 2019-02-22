---
title: 切換中斷點命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 11f0598fa20a5293d662bdbb23b7f67c6c0c80b2
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54793170"
---
# <a name="toggle-breakpoint-command"></a>切換中斷點命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
