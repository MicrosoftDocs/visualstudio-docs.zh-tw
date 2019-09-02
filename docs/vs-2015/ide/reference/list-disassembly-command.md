---
title: 列出反組譯碼命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d361e5231d72df81fae164818bbe8341442c9f89
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199169"
---
# <a name="list-disassembly-command"></a>列出反組譯碼命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

開始偵錯處理序，並可讓您指定處理錯誤的方式。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.ListDisassembly [/count:number] [/endaddress:expression]  
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]  
[/linenumbers:yes|no]  
```  
  
## <a name="switches"></a>參數  
 每個參數都可以使用其完整格式或簡短形式叫用。  
  
 /count: `number` [或] /c: `number` [或] /length: `number` [或] /l: `number`  
 選擇性。 要顯示的指令數目。 預設值為 8。  
  
 /endaddress: `expression` [或] /e: `expression`  
 選擇性。 停止反組譯碼的位址。  
  
 /codebytes:`yes`&#124;`no` [或] /bytes:`yes`&#124;`no` [或] /b:`yes`&#124;`no`  
 選擇性。 指出是否要顯示程式碼位元組。 預設值為 `no`。  
  
 /source:`yes`&#124;`no` [或] /s:`yes`&#124;`no`  
 選擇性。 指出是否要顯示來源程式碼。 預設值為 `no`。  
  
 /symbolnames:`yes`&#124;`no` [或] /names:`yes`&#124;`no` [或] /n:`yes`&#124;`no`  
 選擇性。 指出是否要顯示符號名稱。 預設值為 `yes`。  
  
 [/linenumbers:`yes`&#124;`no`]  
 選擇性。 啟用檢視與原始程式碼建立關聯的行號。 /source 參數的值必須為 `yes` 才能使用 /linenumbers 參數。  
  
## <a name="example"></a>範例  
  
```  
>Debug.ListDisassembly  
```  
  
## <a name="see-also"></a>另請參閱  
 [列出呼叫堆疊命令](../../ide/reference/list-call-stack-command.md)   
 [列出執行緒命令](../../ide/reference/list-threads-command.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
