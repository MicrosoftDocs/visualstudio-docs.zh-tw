---
title: Start 命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f08baa8c27debf6493ca090a2a5e80f02b3da982
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54774451"
---
# <a name="start-command"></a>Start 命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
開始偵錯啟始專案。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.Start [address]  
```  
  
## <a name="arguments"></a>引數  
 `address`  
 選擇性。 程式暫停執行的位址，與原始程式碼中的中斷點類似。 此引數只適用於偵錯模式。  
  
## <a name="remarks"></a>備註  
 **Start** 命令在執行時，會對指定的位址執行 RunToCursor 運算。  
  
## <a name="example"></a>範例  
 此範例會啟動偵錯工具，並忽略任何發生的例外狀況。  
  
```  
>Debug.Start  
```  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
