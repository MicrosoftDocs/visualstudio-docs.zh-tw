---
title: 列出模組命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 26c2a2c07e09863c3320c3c69b8cc093bdf39466
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54790029"
---
# <a name="list-modules-command"></a>列出模組命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
列出目前處理序的模組。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]  
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]  
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]  
```  
  
#### <a name="parameters"></a>參數  
 /Address:`yes|no`  
 選擇性。 指定是否要顯示模組的記憶體位址。 預設值為 `yes`。  
  
 /Name:`yes|no`  
 選擇性。 指定是否要顯示模組的名稱。 預設值為 `yes`。  
  
 /Order:`yes|no`  
 選擇性。 指定是否要顯示模組的順序。 預設值為 `no`。  
  
 /Path:`yes|no`  
 選擇性。 指定是否要顯示模組的路徑。 預設值為 `yes`。  
  
 /Process:`yes|no`  
 選擇性。 指定是否要顯示模組的處理序。 預設值為 `no`。  
  
 /SymbolFile:`yes|no`  
 選擇性。 指定是否要顯示模組的符號檔。 預設值為 `no`。  
  
 /SymbolStatus:`yes|no`  
 選擇性。 指定是否要顯示模組的符號狀態。 預設值為 `yes`。  
  
 /Timestamp:`yes|no`  
 選擇性。 指定是否要顯示模組的時間戳記。 預設值為 `no`。  
  
 /Version:`yes|no`  
 選擇性。 指定是否要顯示模組的版本。 預設值為 `no`。  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 這個範例會列出模組名稱、位址，以及目前處理序的時間戳記。  
  
```  
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no  
```  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [如何：使用模組視窗](../../debugger/how-to-use-the-modules-window.md)
