---
title: "移至命令 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9273cd908a8948b47b818e9c4333cb8bd70fe094
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="go-to-command"></a>移至命令
將游標移至指定的程式行。  
  
## <a name="syntax"></a>語法  
  
```  
Edit.GoTo [linenumber]  
```  
  
## <a name="arguments"></a>引數  
 `linenumber`  
 選擇項。 整數，代表要移至的行號。  
  
## <a name="remarks"></a>備註  
 行編號是從一開始。 如果 `linenumber` 的值小於一，則會顯示第一行。 如果 `linenumber` 的值大於最後一行的行號，則會顯示最後一行。  
  
 如果未指定 `linenumber` 的值，則會顯示 [移至指定行] 對話方塊。  
  
 此命令的別名是 GoToLn。  
  
## <a name="example"></a>範例  
  
```  
>Edit.GoTo 125  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)