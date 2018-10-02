---
title: 符號路徑命令 | Microsoft Docs
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
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b21a745177722160b100d0bbad770c3a74c40ca3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486793"
---
# <a name="symbol-path-command"></a>符號路徑命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[符號路徑命令](https://docs.microsoft.com/visualstudio/ide/reference/symbol-path-command)。  
  
  
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
  
## <a name="see-also"></a>另請參閱  
 [命令視窗](../../ide/reference/command-window.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)



