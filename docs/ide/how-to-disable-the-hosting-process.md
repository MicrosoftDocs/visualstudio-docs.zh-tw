---
title: "如何：停用裝載處理序 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9609f902c11291cd6892cf663ec8a343952ebaab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-disable-the-hosting-process"></a>How to: Disable the Hosting Process
啟用裝載處理序時，可能會影響特定 API 呼叫。 在這些情況下，必須停用裝載處理序來傳回正確的結果。  
  
### <a name="to-disable-the-hosting-process"></a>停用裝載處理序  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中開啟可執行專案。 不會產生可執行檔 (例如，類別庫或服務專案) 的專案沒有此選項。  
  
2.  在 [專案] 功能表上，按一下 [屬性]。  
  
3.  按一下 [偵錯] 索引標籤。  
  
4.  清除 [啟用 Visual Studio 裝載處理序] 核取方塊。  
  
 停用裝載處理序時，無法使用數個偵錯功能，或效能降低。 如需詳細資訊，請參閱[偵錯和裝載處理序](../debugger/debugging-and-the-hosting-process.md)。  
  
 一般情況下，停用裝載處理序時：  
  
-   開始偵錯 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 應用程式所需的時間會增加。  
  
-   設計階段運算式評估無法使用。  
  
-   部分信任偵錯無法使用。  
  
## <a name="see-also"></a>請參閱  
 [偵錯和裝載處理序](../debugger/debugging-and-the-hosting-process.md)   
 [裝載處理序 (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [在應用程式開發期間建置](http://msdn.microsoft.com/en-us/c9497d62-3b7b-4449-88e8-cf27acc9efe6)