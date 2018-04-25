---
title: 列印命令 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66175f8aa1d371386793b892c0ead5b4dd1885b0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="print-command"></a>列印命令
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
  
## <a name="see-also"></a>請參閱  
 [評估陳述式命令](../../ide/reference/evaluate-statement-command.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)