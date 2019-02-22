---
title: Watch 命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b1a04dce73dbf2551b51f2395b3512e62daf3766
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54788186"
---
# <a name="watch-command"></a>Watch 命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
建立並開啟 [監看式]  視窗的指定執行個體。 您可以使用 [監看式] 視窗來計算變數、運算式和暫存器的值，以編輯這些值，以及儲存結果。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.Watch[index]  
```  
  
## <a name="arguments"></a>引數  
 `index`  
 必要項。 監看式視窗的執行個體數目。  
  
## <a name="remarks"></a>備註  
 `index` 必須是整數。 有效值為 1、2、3 或 4。  
  
## <a name="example"></a>範例  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>請參閱  
 [[自動變數] 和 [區域變數] 視窗](../../debugger/autos-and-locals-windows.md)   
 [如何：編輯變數視窗中的值](http://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5)   
 [如何：使用快速監看式對話方塊](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
