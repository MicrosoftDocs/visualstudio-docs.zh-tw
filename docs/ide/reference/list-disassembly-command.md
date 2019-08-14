---
title: 列出反組譯碼命令
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6dc4bddefe0240a8e53babeec1fdce4f83ce5ef1
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926215"
---
# <a name="list-disassembly-command"></a>列出反組譯碼命令
開始偵錯處理序，並可讓您指定處理錯誤的方式。

## <a name="syntax"></a>語法

```cmd
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

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>另請參閱

- [列出呼叫堆疊命令](../../ide/reference/list-call-stack-command.md)
- [列出執行緒命令](../../ide/reference/list-threads-command.md)
- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)