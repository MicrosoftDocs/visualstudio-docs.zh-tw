---
title: 列出原始碼命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ae2ed3e8a9c07d59f5b1c2fe2350956a54dfaa66
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54761503"
---
# <a name="list-source-command"></a>列出原始碼命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
顯示指定的原始程式碼程式行。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.ListSource [/Count:number] [/Current] [/File:filename]  
[/Line:number] [/ShowLineNumbers:yes|no]  
```  
  
## <a name="switches"></a>參數  
 /Count:`number`  
 選擇性。 指定要顯示的行數。  
  
 /Current  
 選擇性。 顯示目前這行。  
  
 /File:`filename`  
 選擇性。 要顯示之檔案的路徑。 如果未指定檔名，則此命令會顯示目前陳述式行的原始程式碼。  
  
 /Line:`number`  
 選擇性。 顯示特定行號。  
  
 /ShowLineNumbers:`yes|no`  
 選擇性。 指定是否顯示行號。  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 此範例列出 Form1.vb 檔案第 4 行的原始程式碼，並顯示行號。  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)
