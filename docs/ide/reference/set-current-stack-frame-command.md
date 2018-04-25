---
title: 設定目前堆疊框架命令 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f8851530dec3e5e1a2c3e829c1508155a2dbda8a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="set-current-stack-frame-command"></a>設定目前堆疊框架命令
可讓您設定特定堆疊框架。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.SetCurrentStackFrame index  
```  
  
## <a name="arguments"></a>引數  
 `index`  
 必要。 依索引選取堆疊框架。  
  
## <a name="example"></a>範例  
  
```  
>Debug.SetCurrentStackFrame 1  
```  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)