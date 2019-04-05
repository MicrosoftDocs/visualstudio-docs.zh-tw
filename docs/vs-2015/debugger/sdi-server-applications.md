---
title: SDI 伺服器應用程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1296c0f43d0409df0081861095c5ec068932bbc1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942381"
---
# <a name="sdi-server-applications"></a>SDI 伺服器應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您要對 SDI 伺服器應用程式進行偵錯，則必須在 C/C++、C# 或 Visual Basic 專案之 [專案] 屬性頁對話方塊的 [命令列引數] 屬性中，指定 `/Embedding` 或 `/Automation`。  
  
 透過這些命令列的引數，偵錯工具可以啟動伺服器應用程式，就如同它是由容器所啟動。 從程式管理員或檔案管理員啟動容器，將導致容器使用由偵錯工具啟動的伺服器執行個體。  
  
## <a name="finding-the-command-line-arguments-property"></a>找出命令列引數屬性  
 若要存取 [專案] 屬性頁對話方塊，請在 [方案總管] 中用滑鼠右鍵按一下您的專案，然後從捷徑功能表選擇 [屬性]。 若要尋找 [命令列的引數] 屬性，請展開 [組態屬性] 分類，然後按一下 [偵錯] 頁。  
  
## <a name="see-also"></a>另請參閱  
 [對 COM 和 ActiveX 進行偵錯](../debugger/com-and-activex-debugging.md)   
 [如何：針對 COM 伺服器進行偵錯](../debugger/how-to-debug-com-servers.md)
