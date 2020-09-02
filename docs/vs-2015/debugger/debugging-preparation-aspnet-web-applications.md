---
title: 偵錯工具準備： ASP.NET Web 應用程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7a80587062442688551d07128a2cec49a712adf6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691455"
---
# <a name="debugging-preparation-aspnet-web-applications"></a>偵錯準備：ASP.NET Web 應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

網站 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 範本會建立 Web 表單應用程式。 當您使用這種範本建立網站時，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會建立偵錯的預設設定。 在 [ **專案屬性** ] 對話方塊中，您可以指定是否要讓網頁成為啟動頁面。 當您開始 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 使用這些預設設定來進行網站的偵錯工具時，會 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 啟動 Internet Explorer，並將偵錯工具附加至背景 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 工作進程 ( # A0 或 w3wp.exe) 。 如需詳細資訊，請參閱[系統需求](../debugger/aspnet-debugging-system-requirements.md)。  
  
### <a name="to-create-a-web-forms-application"></a>若要建立 Web Form 網頁  
  
1. 在 [檔案 **] 功能表上，選擇 [** **新網站**]。  
  
2. 在 [**新**網站] 對話方塊中，選取 [ [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] **網站**]。  
  
3. 按一下 [確定]  。  
  
### <a name="to-debug-your-web-form"></a>若要偵錯 Web Form  
  
1. 在函式和事件處理常式中設定一個或多個中斷點。  
  
     如需詳細資訊，請參閱 [Breakpoints and Tracepoints](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)。  
  
2. 遇到中斷點時，逐步執行函式內的程式碼。 請觀察程式碼的執行，直到您找出問題癥結。  
  
     如需詳細資訊，請參閱 [逐步執行](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9) 和偵測 [Web 應用程式和腳本](../debugger/debugging-web-applications-and-script.md)。  
  
## <a name="changing-default-configurations"></a>變更預設的組態  
 如果想要變更 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 建立的預設偵錯和發行組態，您可以自行變更。 如需詳細資訊，請參閱[如何：設定偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)。  
  
#### <a name="to-change-the-default-debug-configuration"></a>若要變更預設偵錯組態  
  
1. 在 **方案總管**中，以滑鼠右鍵按一下網站，然後選取 [ **屬性頁** ] 以開啟 [ **屬性頁** ] 對話方塊。  
  
2. 按一下 [ **開始選項**]。  
  
3. 將 [ **啟動動作** ] 設定為應先顯示的網頁。  
  
4. 在 **[偵錯工具] 底下，確定**已選取 [ **ASP.NET] 調試** 程式。  
  
     如需詳細資訊，請參閱 [Web 專案的屬性頁設定](../debugger/property-pages-settings-for-web-projects.md)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具設定和準備](../debugger/debugger-settings-and-preparation.md)   
 [偵錯工具基本概念](../debugger/debugger-basics.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)
