---
title: 偵錯原生程式碼中的執行緒的秘訣 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06e8690583794c23ce95fb52ef6cab3ab6667afe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49184921"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>在機器碼中偵錯執行緒的秘訣
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在機器碼中對執行緒執行偵錯時，有下列幾個訣竅：  
  
-   您可以輸入，以檢視執行緒資訊區塊的內容`@TIB`中**監看式**視窗或**快速監看式** 對話方塊。  
  
-   您可以輸入，以檢視目前執行緒的最後一個錯誤碼`@Err`中**監看式**視窗或**快速監看式** 對話方塊。  
  
-   C 執行階段程式庫 (CRT) 功能可能有助於執行多執行緒應用程式偵錯。 如需詳細資訊，請參閱 [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)



