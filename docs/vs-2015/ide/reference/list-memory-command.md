---
title: 列出記憶體命令 | Microsoft Docs
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
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d2a440c43ad4bfaf5791a60422533a04bed21d72
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499298"
---
# <a name="list-memory-command"></a>列出記憶體命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[列出記憶體命令](https://docs.microsoft.com/visualstudio/ide/reference/list-memory-command)。  
  
  
顯示指定的記憶體範圍的內容。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]  
[/Hex|Signed|Unsigned] [expression]  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 選擇性。 要從其中開始顯示記憶體的記憶體位址。  
  
## <a name="switches"></a>參數  
 /ANSI&#124;Unicode  
 選擇性。 顯示對應到記憶體位元組的記憶體字元，ANSI 或 Unicode。  
  
 /Count:`number`  
 選擇性。 決定要顯示多少個位元組的記憶體，從 `expression` 開始。  
  
 /Format:`formattype`  
 選擇性。 在 [記憶體] 視窗中檢視記憶體資訊用的格式類型，可能是 OneByte、TwoBytes、FourBytes、EightBytes、Float (32 位元) 或 Double (64 位元)。 如果使用 OneByte，則無法使用 `/Unicode`。  
  
 /Hex&#124;Signed&#124;Unsigned  
 選擇性。 指定檢視數字的格式：帶正負號、不帶正負號，或十六進位。  
  
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
|**db**|Debug.ListMemory /Format:OneByte|  
|**dc**|Debug.ListMemory /Format:FourBytes /Ansi|  
|**dd**|Debug.ListMemory /Format:FourBytes|  
|**df**|Debug.ListMemory /Format:Float|  
|**dq**|Debug.ListMemory /Format:EightBytes|  
|**du**|Debug.ListMemory /Unicode|  
  
## <a name="example"></a>範例  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
## <a name="see-also"></a>另請參閱  
 [列出呼叫堆疊命令](../../ide/reference/list-call-stack-command.md)   
 [列出執行緒命令](../../ide/reference/list-threads-command.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)




