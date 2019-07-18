---
title: 列印命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 65d78387c6d60d0b432db9aab175fbfe8dc2869b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203557"
---
# <a name="print-command"></a>列印命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

評估運算式，或顯示指定的文字。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>引數  
 `text`  
 必要項。 要評估的運算式或要顯示的文字。  
  
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
