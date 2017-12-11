---
title: "升級 Visual Studio 2010 的自動程式化 UI 測試 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11232a83-73ea-46bd-bc0c-46f74f6e3a42
caps.latest.revision: "33"
ms.author: douge
manager: douge
ms.openlocfilehash: 8b854bcfcb7227a454023f89ce732706b1e545cc
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2017
---
# <a name="upgrading-coded-ui-tests-from-visual-studio-2010"></a>升級 Visual Studio 2010 的自動程式化 UI 測試
包含建立於 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 中之自動程式化 UI 測試的測試專案在 Visual Studio 2012 或更新版本中開啟時，會以無訊息模式修復。 如果已將測試專案簽入原始檔控制，則專案檔會簽出此修復。 一旦修復，這些包含自動程式碼 UI 測試的測試專案可以再次用於 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 和 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]。  
  
 **需求**  
  
-   Visual Studio 企業版  
  
> [!NOTE]
>  Visual Studio 包含一個以上的測試專案類型。 如果您要建立新的自動程式碼 UI 測試，則必須在自動程式碼 UI 測試專案類型中建立。 如需詳細資訊，請參閱 [從舊版 Visual Studio 升級測試](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)。  
  
> [!WARNING]
>  當您在[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 或 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 連同 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 中開啟測試專案，則必須重建包含自動程式碼 UI 測試的 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]個測試專案。  
  
> [!WARNING]
>  在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 中開啟建立於 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]且只包含單元測試的測試專案時，則無法將自動程式碼 UI 測試新增至其中。 同樣地，您無法將自動程式碼 UI 測試新增至建立於 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]中的單元測試專案。  
  
## <a name="compatibility-issues-between-visual-studio-2010-and-visual-studio-2012-or-later"></a>Visual Studio 2010 和 Visual Studio 2012 或更新版本之間的相容性問題  
 下表列出在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 和 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]之間移轉自動程式碼 UI 測試時要注意的問題。  
  
> [!CAUTION]
>  在自動程式碼 UI 測試專案中有一個和參考相關的已知問題並未出現在 [方案總管] 中。 如需詳細資訊，請參閱包含在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 安裝媒體上的讀我檔案。  
  
|自動程式碼 UI 功能|問題|方案|  
|----------------------------|-----------|--------------|  
|[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|**建置將會失敗**<br /><br /> 如果您有 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] Feature Pack 2，並已針對 Silverlight 應用程式建立自動程式碼 UI 測試專案，這些專案無法在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]中開啟。|建議您只在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] Feature Pack 2 管理這些專案。|  
|[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|**建置會成功，測試回合將會失敗**<br /><br /> 如果您有 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] Feature Pack 2，並已針對 Firefox 中的 web 應用程式建立自動程式碼 UI 測試專案，這些專案無法在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]中開啟。|建議您只在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] Feature Pack 2 管理這些專案。|  
|已在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]中新增新的 UI 程式碼測試 API|**建置將會失敗**<br /><br /> 如果您使用 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]中的新 UI 測試 API 建立自動程式碼 UI 測試，這些專案無法在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]中開啟。|使用新 API 的專案只能在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中管理。|  
|在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 中，參考新增於 csproj 檔案中的 'Choose' 陳述式內。 在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]中，我們使用意見反應目標檔案包含自動程式碼 UI 測試組件參考。|在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]中，自動程式碼 UI 測試不能新增至 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] (或 SP1) 中建立的測試專案，該專案不包含自動程式碼 UI 測試。<br /><br /> 修復程序會新增目標檔案和選擇陳述式。 如果自動程式碼 UI 測試不在測試專案中，則專案會標記為已修復，在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]中新增自動程式碼 UI 測試時，就不會加入適當的參考。|您必須在相同的方案中使用 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 建立新的測試專案並在其中新增新的自動程式碼 UI 測試。 或者，您可以將自動程式碼 UI 測試新增至 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 中的測試專案並在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]中開啟該專案。|  
  
##  <a name="UpgradingCodedUIFromVS2010_Update"></a> Visual Studio 2010 SP1 Update  
 現已提供 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] SP1 的更新，包含 Visual Studio 2012 或更新版本和 Windows 8 或更新版本的相容性支援，可以在 [Microsoft 下載中心](http://www.microsoft.com/download/details.aspx?id=34677)下載以及作為 Visual Studio 更新。  
  
 套用更新之後，下列 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] SP1 自動程式碼 UI 測試工具功能已針對 Windows 8 改進：  
  
-   您可以在執行 Windows 8 的電腦上，針對 Microsoft .NET Framework 4.5 架構的 Windows Presentation Foundation (WPF) 控制項執行自動程式碼 UI 測試。  
  
-   您可以在執行 Windows 8 的電腦上，針對 64 位元 (x64) Internet Explorer 10 執行自動程式碼 UI 測試。  
  
 此更新中修復了下列問題：  
  
-   **程式碼涵蓋範圍：** 無法開啟由 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] SP1 中的 Visual Studio 2012 所建立的程式碼涵蓋範圍檔案 (.coverage)。  
  
-   **受困的測試成品：** 您的小組擁有指派給 Team Foundation Server (TFS) 2010 中無效使用者的測試成品。 例如，使用者已離開公司，但仍有指派給該使用者的測試案例。 您從 TFS 2010 升級為 TFS 2012。 您使用 [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 2010 連接至升級的 TFS 伺服器。 您無法使用 [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 2010 將測試成品指派給任何 TFS 使用者。  
  
-   **負載測試：** 當您在執行 Windows 8 的電腦上執行負載測試，而網路類型並非區域網路 (LAN) 設定檔時，網路模擬器驅動程式會造成作業系統當機。 如需詳細資訊，請參閱 [知識庫文件 2736182](http://support.microsoft.com/kb/2736182)。  
  
## <a name="see-also"></a>另請參閱  
 [移植、移轉和升級 Visual Studio 專案](../porting/port-migrate-and-upgrade-visual-studio-projects.md)   
 [從舊版 Visual Studio 升級測試](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)   
 [使用使用者介面自動化來測試您的程式碼](../test/use-ui-automation-to-test-your-code.md)   
 [從現有的動作記錄產生自動程式化 UI 測試](/devops-test-docs/test/generating-a-coded-ui-test-from-an-existing-action-recording)   
 [自動程式化 UI 測試和動作記錄的支援組態和平台](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
