---
title: 評估陳述式命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f774458eb63d9e56b99a635e7b32309375a903ef
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59669233"
---
# <a name="evaluate-statement-command"></a>評估陳述式命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

評估並顯示指定的陳述式。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.EvaluateStatement text   
```  
  
## <a name="arguments"></a>引數  
 `text`  
 必要項。 要評估的陳述式。  
  
## <a name="remarks"></a>備註  
 用來輸入 **EvaluateStatement** 命令的視窗可判斷是否將等號 (=) 解譯為比較運算子或指派運算子。  
  
 在 [命令] 視窗中，等號 (=) 會解譯為比較運算子。 因此；例如，如果 `a` 和 `b` 變數的值不同，則命令  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 會傳回值 `false`。  
  
 相較之下，在 [即時運算] 視窗中，等號 (=) 會解譯為指派運算子。 因此；例如，命令  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 會將 `b` 變數的值指派給變數 `a`。  
  
## <a name="example"></a>範例  
  
```  
>Debug.EvaluateStatement(a+b)  
```  
  
## <a name="see-also"></a>請參閱  
 [列印命令](../../ide/reference/print-command.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
