---
title: 如何： 偵錯 Web 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- Web services, debugging
- ASP.NET Web Forms, debugging
- ASP.NET, debugging Web applications
- debugging ASP.NET Web applications, during development
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 40
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3dce1129282dc7273631e261bb32d313f65ce381
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487557"
---
# <a name="how-to-debug-web-applications"></a>如何：偵錯 Web 應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 偵錯 Web 應用程式](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-web-applications)。  
  
[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 是開發 Web 應用程式中的主要技術[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 偵錯工具提供在本機環境或遠端伺服器上，偵錯 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web 應用程式所用的強大工具。 本主題描述如何偵錯[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]在開發期間的專案。 如需如何偵錯資訊[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Web 應用程式已部署在實際執行伺服器上，請參閱 <<c2> [ 偵錯部署 Web 應用程式](../debugger/debugging-deployed-web-applications.md)。  
  
 若要偵錯 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 應用程式：  
  
-   您必須具有必要的使用權限。 如需詳細資訊，請參閱 <<c0> [ 系統需求](../debugger/aspnet-debugging-system-requirements.md)。  
  
-   [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 偵錯必須在啟用**專案屬性**。  
  
-   應用程式的組態檔 (Web.config) 必須設為偵錯模式。 偵錯模式會導致 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 產生動態產生之檔案的符號，並使偵錯工具附加到 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 應用程式。 如果您已從 Web 專案範本建立專案，則 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會在開始偵錯時自動設定這個項目。  
  
-   如需詳細資訊，請參閱 <<c0> [ 如何： 啟用 ASP.NET 應用程式的偵錯](../debugger/how-to-enable-debugging-for-aspnet-applications.md)。  
  
### <a name="to-debug-a-web-application-during-development"></a>若要在開發期間偵錯 Web 應用程式  
  
1.  在 [**偵錯**] 功能表中，按一下**開始**開始偵錯 Web 應用程式。  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會建置 Web 應用程式專案、視需要部署應用程式、如果您在本機偵錯，則會啟動 ASP.NET 程式開發伺服器，以及附加至 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 背景工作處理序。  
  
2.  使用偵錯工具來設定和清除中斷點、逐步執行和執行其他偵錯作業，就和您使用任何應用程式一樣。  
  
     如需詳細資訊，請參閱 <<c0> [ 偵錯工具基本概念](../debugger/debugger-basics.md)。  
  
3.  在上**偵錯**] 功能表中，按一下**停止偵錯**端偵錯工作階段中，或上**檔案**功能表中 Internet Explorer 中，按一下 [**關閉**。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 Web 應用程式和指令碼](../debugger/debugging-web-applications-and-script.md)   
 [偵錯 ASP.NET 和 AJAX 應用程式](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [如何：啟用 ASP.NET 應用程式的偵錯](../debugger/how-to-enable-debugging-for-aspnet-applications.md)



