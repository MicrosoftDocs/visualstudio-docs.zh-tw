---
title: SDI 伺服器應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9047c9b39bad5f4f790327b5ee65b4de688db9d8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475658"
---
# <a name="sdi-server-applications"></a>SDI 伺服器應用程式
如果您正在偵錯 SDI 伺服器應用程式，您必須指定`/Embedding`或`/Automation`中**命令列引數**屬性*專案*屬性頁對話方塊中，C/c + +、 C# 中，或Visual Basic 專案。  
  
 透過這些命令列的引數，偵錯工具可以啟動伺服器應用程式，就如同它是由容器所啟動。 從程式管理員或檔案管理員啟動容器，將導致容器使用由偵錯工具啟動的伺服器執行個體。  
  
## <a name="finding-the-command-line-arguments-property"></a>找出命令列引數屬性  
 若要存取*專案*屬性頁 對話方塊中，以滑鼠右鍵按一下方案總管 中的專案，並從捷徑功能表，然後選擇 屬性。 若要尋找 [命令列的引數] 屬性，請展開 [組態屬性] 分類，然後按一下 [偵錯] 頁。  
  
## <a name="see-also"></a>另請參閱  
 [COM 和 ActiveX 的偵錯](../debugger/com-and-activex-debugging.md)   
 [如何：偵錯 COM 伺服器](../debugger/how-to-debug-com-servers.md)