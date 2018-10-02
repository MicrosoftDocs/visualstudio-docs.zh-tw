---
title: 偵錯準備： ASP.NET Web 應用程式 |Microsoft Docs
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
- VB
- CSharp
helpviewer_keywords:
- debugging ASP.NET Web applications
- debugging [Visual Studio], Web applications
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 38
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20731f5036a89c3c19fbea0d825d67fc02c13cf9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491536"
---
# <a name="debugging-preparation-aspnet-web-applications"></a>偵錯準備：ASP.NET Web 應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[偵錯準備： ASP.NET Web 應用程式](https://docs.microsoft.com/visualstudio/debugger/debugging-preparation-aspnet-web-applications)。  
  
[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]網站範本會建立 Web Form 應用程式。 當您使用這種範本建立網站時，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會建立偵錯的預設設定。 在 [**專案屬性**] 對話方塊中，您可以指定您是否想要為起始頁的 Web 網頁。 當您啟動偵錯[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]網站上使用這些預設設定，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]啟動 Internet Explorer，並附加偵錯工具[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]背景工作處理序 （aspnet_wp.exe 或 w3wp.exe）。 如需詳細資訊，請參閱 <<c0> [ 系統需求](../debugger/aspnet-debugging-system-requirements.md)。  
  
### <a name="to-create-a-web-forms-application"></a>若要建立 Web Form 網頁  
  
1.  在 **檔案**功能表上，選擇**新的網站**。  
  
2.  在  **New Web Site**對話方塊中，選取[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]**網站**。  
  
3.  按一下 [確定 **Deploying Office Solutions**]。  
  
### <a name="to-debug-your-web-form"></a>若要偵錯 Web Form  
  
1.  在函式和事件處理常式中設定一個或多個中斷點。  
  
     如需詳細資訊，請參閱 [Breakpoints and Tracepoints](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)。  
  
2.  遇到中斷點時，逐步執行函式內的程式碼。 請觀察程式碼的執行，直到您找出問題癥結。  
  
     如需詳細資訊，請參閱 <<c0> [ 逐步執行程式碼](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9)並[偵錯 Web 應用程式和指令碼](../debugger/debugging-web-applications-and-script.md)。  
  
## <a name="changing-default-configurations"></a>變更預設的組態  
 如果想要變更 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 建立的預設偵錯和發行組態，您可以自行變更。 如需詳細資訊，請參閱[如何：設定偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)。  
  
#### <a name="to-change-the-default-debug-configuration"></a>若要變更預設偵錯組態  
  
1.  在**方案總管**，以滑鼠右鍵按一下網站，然後選取**屬性頁**以開啟**屬性頁** 對話方塊。  
  
2.  按一下 **啟動選項**。  
  
3.  設定**起始動作**應該會顯示之 Web 網頁。  
  
4.  底下**偵錯工具**，請確定**ASP.NET 偵錯**已選取。  
  
     如需詳細資訊，請參閱 < [Web 專案的屬性頁設定](../debugger/property-pages-settings-for-web-projects.md)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)   
 [偵錯工具基礎](../debugger/debugger-basics.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)



