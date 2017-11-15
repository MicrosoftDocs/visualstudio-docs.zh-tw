---
title: "設定基數命令 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 060221e5abe0ff9082a04f8b75561a7e4dec9f64
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="set-radix-command"></a>設定基數命令
設定或傳回用來顯示整數值的數值基底。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## <a name="arguments"></a>引數  
 `10`、`16`、`hex` 或 `dec`  
 選擇項。 表示十進位 (10 或 dec) 或十六進位 (16 或 hex)。 如果省略引數，則會傳回目前基數值。  
  
## <a name="example"></a>範例  
 此範例設定環境以十六進位格式顯示整數值。  
  
```  
>Debug.SetRadix hex  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)