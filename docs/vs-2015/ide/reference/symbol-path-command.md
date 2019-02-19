---
title: 符號路徑命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: da136a76a06182bd32ebf2ca868e77f202087e45
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54767275"
---
# <a name="symbol-path-command"></a>符號路徑命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
設定目錄清單，以讓偵錯工具搜尋符號。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## <a name="arguments"></a>引數  
 `pathname`  
 選擇性。 讓偵錯工具搜尋符號的路徑清單 (以分號分隔)。  
  
## <a name="remarks"></a>備註  
 如果未指定 `pathname`，則此命令會列出目前符號路徑。  
  
## <a name="example"></a>範例  
 此範例會將兩個路徑新增至符號目錄清單。  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## <a name="example"></a>範例  
 此範例會顯示以分號分隔的目前符號路徑清單。  
  
```  
Debug.SymbolPath  
```  
  
## <a name="see-also"></a>請參閱  
 [命令視窗](../../ide/reference/command-window.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
