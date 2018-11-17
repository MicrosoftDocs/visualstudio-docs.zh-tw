---
title: SDI 伺服器應用程式 |Microsoft Docs
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
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea0497c7d20c0102aff3bc77cdecf87d1525a82c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752414"
---
# <a name="sdi-server-applications"></a>SDI 伺服器應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您正在偵錯對 SDI 伺服器應用程式，您必須指定`/Embedding`或是`/Automation`中**命令列引數**中的屬性*專案*屬性頁 對話方塊中，C/c + +、 C# 中，或Visual Basic 專案。  
  
 透過這些命令列的引數，偵錯工具可以啟動伺服器應用程式，就如同它是由容器所啟動。 從程式管理員或檔案管理員啟動容器，將導致容器使用由偵錯工具啟動的伺服器執行個體。  
  
## <a name="finding-the-command-line-arguments-property"></a>找出命令列引數屬性  
 若要存取*專案*屬性頁 對話方塊中，以滑鼠右鍵按一下方案總管 中的專案，並從捷徑功能表，然後選擇 屬性。 若要尋找 [命令列的引數] 屬性，請展開 [組態屬性] 分類，然後按一下 [偵錯] 頁。  
  
## <a name="see-also"></a>另請參閱  
 [COM 和 ActiveX 進行偵錯](../debugger/com-and-activex-debugging.md)   
 [如何：偵錯 COM 伺服器](../debugger/how-to-debug-com-servers.md)



