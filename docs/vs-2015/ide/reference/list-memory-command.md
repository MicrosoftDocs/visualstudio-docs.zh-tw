---
title: 列出記憶體命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2630402e03d1256f63e542818a9066745206d2c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672752"
---
# <a name="list-memory-command"></a>列出記憶體命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

顯示指定的記憶體範圍的內容。

## <a name="syntax"></a>語法

```
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>引數
 `expression` 選擇項。 要從其中開始顯示記憶體的記憶體位址。

## <a name="switches"></a>交換器
 /ANSI&#124;Unicode 選擇性。 顯示對應到記憶體位元組的記憶體字元，ANSI 或 Unicode。

 /Count： `number` 選擇性。 決定要顯示多少個位元組的記憶體，從 `expression` 開始。

 /Format： `formattype` 選擇性。 在 [記憶體]**** 視窗中檢視記憶體資訊用的格式類型，可能是 OneByte、TwoBytes、FourBytes、EightBytes、Float (32 位元) 或 Double (64 位元)。 如果使用 OneByte，則無法使用 `/Unicode`。

 /Hex&#124;簽署&#124;不帶正負號的選用。 指定檢視數字的格式：帶正負號、不帶正負號，或十六進位。

## <a name="remarks"></a>備註
 您不必寫出完整的 **Debug.ListMemory** 命令與所有參數，而可以使用預先定義的別名叫用命令，並將特定的參數預設為指定的值。 例如，若不輸入：

```
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

 您可以撰寫：

```
>df /Count:30 /Unicode
```

 以下是 **Debug.ListMemory** 命令可用的別名清單：

|Alias|命令和參數|
|-----------|--------------------------|
|**d**|Debug.ListMemory|
|**da**|Debug.ListMemory /Ansi|
|**Db**|Debug.ListMemory /Format:OneByte|
|**直流**|Debug.ListMemory /Format:FourBytes /Ansi|
|**dd**|Debug.ListMemory /Format:FourBytes|
|**Df**|Debug.ListMemory /Format:Float|
|**Dq**|Debug.ListMemory /Format:EightBytes|
|**du**|Debug.ListMemory /Unicode|

## <a name="example"></a>範例

```
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>另請參閱
 [列出呼叫堆疊命令](../../ide/reference/list-call-stack-command.md)[清單執行緒命令](../../ide/reference/list-threads-command.md) [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)[命令視窗](../../ide/reference/command-window.md)[尋找/命令](../../ide/find-command-box.md)方塊[Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
