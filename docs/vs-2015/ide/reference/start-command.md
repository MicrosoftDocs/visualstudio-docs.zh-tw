---
title: Start 命令 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a3b2f482fb33664796a4e6fe451a6a2917e9592f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247697"
---
# <a name="start-command"></a>Start 命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
開始偵錯啟始專案。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.Start [address]  
```  
  
## <a name="arguments"></a>引數  
 `address`  
 選擇性。 程式暫停執行的位址，與原始程式碼中的中斷點類似。 此引數只適用於偵錯模式。  
  
## <a name="remarks"></a>備註  
 **Start** 命令在執行時，會對指定的位址執行 RunToCursor 運算。  
  
## <a name="example"></a>範例  
 此範例會啟動偵錯工具，並忽略任何發生的例外狀況。  
  
```  
>Debug.Start  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



