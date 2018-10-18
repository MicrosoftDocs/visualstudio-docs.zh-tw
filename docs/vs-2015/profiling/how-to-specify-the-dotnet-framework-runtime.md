---
title: 如何︰指定 .NET Framework 執行階段 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2508d9b0a7ab1c2511dd1bbe2a46ea486ce86a32
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189276"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>如何︰指定 .NET Framework 執行階段
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用 [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] 版本，應用程式就可以由使用不同版本的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 執行階段所建置的模組組成。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 程式碼剖析工具預設會對應用程式所載入的第一個執行階段進行程式碼剖析。 當您以程式碼剖析工具啟動應用程式時，以及當您將程式碼剖析工具附加至已在執行的應用程式時，都可以指定要進行程式碼剖析的執行階段。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>在使用程式碼剖析工具來啟動應用程式時，指定要進行程式碼剖析的 .NET Framework 執行階段  
  
1.  在 [效能總管] 中，以滑鼠右鍵按一下效能工作階段，按一下 [屬性]，然後按一下 [進階]。  
  
     [目標 CLR 版本] 清單方塊會顯示 [自動]，以及電腦上安裝的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 執行階段的版本。  
  
2.  請執行下列其中一個步驟：  
  
    -   按一下您要進行程式碼剖析的 CLR 版本。  
  
    -   按一下 [自動]，對應用程式所載入的第一個執行階段進行程式碼剖析。  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>在將程式碼剖析工具附加至應用程式時，指定要進行程式碼剖析的 .NET Framework 執行階段  
  
1.  在 [分析] 功能表上，指向 [程式碼剖析工具]，然後按一下 [附加/中斷連結]。  
  
2.  在 [將程式碼剖析工具附加至處理序] 對話方塊中，按一下您要進行程式碼剖析的處理序。  
  
     [目標 CLR 版本] 清單方塊會顯示 [自動]，以及電腦上安裝的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 執行階段的版本。  
  
3.  請執行下列其中一個步驟：  
  
    -   按一下您要進行程式碼剖析的 CLR 版本。  
  
    -   按一下 [自動]，對程式碼剖析工具附加至應用程式時所載入的版本進行程式碼剖析。



