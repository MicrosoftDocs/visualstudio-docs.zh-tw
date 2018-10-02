---
title: 列印命令 | Microsoft Docs
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
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e518b3c6ffc3520b408e7c1bfb1fd1703e40a8de
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488195"
---
# <a name="print-command"></a>列印命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[Print 命令](https://docs.microsoft.com/visualstudio/ide/reference/print-command)。  
  
  
評估運算式，或顯示指定的文字。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>引數  
 `text`  
 必要。 要評估的運算式或要顯示的文字。  
  
## <a name="remarks"></a>備註  
 您可以使用問號 (?) 作為此命令的別名。 因此；例如，命令  
  
```  
>Debug.Print expA  
```  
  
 也可以寫成  
  
```  
>? expA  
```  
  
 此命令的兩個版本都會傳回 `expA` 運算式的目前值。  
  
## <a name="example"></a>範例  
  
```  
>Debug.Print varA  
```  
  
## <a name="see-also"></a>另請參閱  
 [評估陳述式命令](../../ide/reference/evaluate-statement-command.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)



