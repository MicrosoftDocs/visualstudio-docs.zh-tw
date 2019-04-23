---
title: 設定基數命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bee6368931dc47b78186ec870039ab292960fa77
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59654070"
---
# <a name="set-radix-command"></a>設定基數命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

設定或傳回用來顯示整數值的數值基底。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## <a name="arguments"></a>引數  
 `10`、`16`、`hex` 或 `dec`  
 選擇性。 表示十進位 (10 或 dec) 或十六進位 (16 或 hex)。 如果省略引數，則會傳回目前基數值。  
  
## <a name="example"></a>範例  
 此範例設定環境以十六進位格式顯示整數值。  
  
```  
>Debug.SetRadix hex  
```  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
