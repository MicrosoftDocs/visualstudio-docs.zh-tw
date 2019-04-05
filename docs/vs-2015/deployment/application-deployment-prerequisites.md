---
title: 應用程式部署必要條件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, platform detection
- ClickOnce deployment, prerequisites
- ClickOnce deployment, dependencies
- prerequisites, ClickOnce
- dependencies, ClickOnce
ms.assetid: fc6e047e-ad94-44e8-8ff5-b6d1f4ca7735
caps.latest.revision: 53
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0c76ed1b24350a10891df69687080988603553fa
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942124"
---
# <a name="application-deployment-prerequisites"></a>應用程式部署必要條件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

為了確保應用程式順利安裝及執行，您必須先確認目標電腦上已安裝與應用程式相依的所有元件。 例如，使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 建立的大多數應用程式都與 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 具相依性；在安裝應用程式之前，目的地電腦上必須存在正確的 Common Language Runtime 版本。  
  
 您可以選取這些先決條件**Prerequisites Dialog Box**和安裝.NET Framework，以及其他可轉散發套件安裝的一部分。 這個做法稱為啟動載入。 下一步[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]會產生 Windows 可執行程式，也就是名為 Setup.exe*啟動載入器*。 啟動載入器負責在應用程式執行前安裝這些必要條件。 如需有關如何選取這些必要條件的詳細資訊，請參閱 < [Prerequisites Dialog Box](../ide/reference/prerequisites-dialog-box.md)。  
  
 每個必要條件都是啟動載入器套件。 啟動載入器套件是一組目錄和檔案，內含描述必要條件安裝方式的資訊清單檔案。 如果 [必要條件] 對話方塊中未列出您應用程式的必要條件，您可以建立自訂啟動載入器套件並將必要條件新增至 Visual Studio。 然後即可在 [必要條件] 對話方塊中選取必要條件。 如需詳細資訊，請參閱 <<c0> [ 建立啟動載入器套件](../deployment/creating-bootstrapper-packages.md)。  
  
 ClickOnce 部署預設會啟用啟動載入。 針對 ClickOnce 部署產生的啟動載入器會經過簽署。 您可以停用元件的啟動載入，不過只有在您確定所有目標電腦上都已安裝正確版本的元件時，才應該這樣做。  
  
## <a name="bootstrapping-and-clickonce-deployment"></a>啟動載入和 ClickOnce 部署  
 在用戶端電腦上安裝應用程式之前，[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 會檢查用戶端，確定該用戶端具有應用程式資訊清單中所指定的特定需求。 這些需求包括下列各項：  
  
- Common Language Runtime 的最小必要版本，在應用程式資訊清單中會指定為一個組件相依性。  
  
- 應用程式所需之 Windows 作業系統的最小必要版本，如應用程式資訊清單中的 `<osVersionInfo>` 項目所指定。 (請參閱[\<相依性 > 項目](../deployment/dependency-element-clickonce-application.md))  
  
- 您必須在全域組件快取 (GAC) 中預先安裝所有組件的最小版本，如組件資訊清單中的組件相依性宣告所指定。  
  
  [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 可以偵測遺漏的必要條件，然後您可以使用啟動載入器，以便安裝必要條件。 如需詳細資訊，請參閱[如何：使用 ClickOnce 應用程式安裝必要條件](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)。  
  
> [!NOTE]
>  若要變更 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 和 MageUI.exe 等工具所產生之資訊清單中的值，您需要在文字編輯器中編輯應用程式資訊清單，然後重新簽署應用程式資訊清單和部署資訊清單。 如需詳細資訊，請參閱[如何：重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。  
  
 如果您使用 Visual Studio 和 ClickOnce 部署應用程式，預設會根據方案中的 .NET Framework 版本來選取啟動載入器套件。 但是，如果您變更目標 .NET Framework 版本，則必須手動更新 [必要條件] 對話方塊中的選項。  
  
|目標 .NET Framework|選取的啟動載入器套件|  
|---------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|  
  
 使用 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 部署時，由 [[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 發行精靈] 所產生的 Publish.htm 網頁會指向只安裝應用程式的連結，或是指向同時安裝應用程式和啟動載入之元件的連結。  
  
 如果您使用 [ClickOnce 發行精靈] 或 Visual Studio 中的 [發行] 頁面產生啟動載入器，將會自動簽署 Setup.exe。 但是，如果您要使用客戶的憑證來簽署啟動載入器，則可以稍後再簽署這個檔案。  
  
## <a name="bootstrapping-and-msbuild"></a>啟動載入和 MSBuild  
 如果您不是使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，而是在命令列上編譯應用程式，您可以使用 Microsoft Build Engine (MSBuild) 工作來建立 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 啟動載入應用程式。 如需詳細資訊，請參閱 < [GenerateBootstrapper 工作](../msbuild/generatebootstrapper-task.md)。  
  
 您也可以使用電子軟體散發系統 (例如 Microsoft Systems Management Server (SMS)) 來預先部署元件，而不使用啟動載入。  
  
## <a name="bootstrapper-setupexe-command-line-arguments"></a>啟動載入器 (Setup.exe) 命令列引數  
 由 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 和 MSBuild 工作所產生的 Setup.exe 可支援下列一小組命令列引數。 超出這些範圍之任何提供給啟動載入應用程式的引數，都會轉送至應用程式安裝程式。  
  
 如果您變更任何啟動載入器選項，則必須變更未簽署的啟動載入器，稍後再簽署啟動載入器檔案。  
  
|命令列引數|描述|  
|---------------------------|-----------------|  
|**-?, -h, -help**|顯示 [說明] 對話方塊。|  
|**-url, -componentsurl**|顯示此安裝程式的儲存 URL 和元件 URL。|  
|**-url=** `location`|設定 Setup.exe 將在其中尋找 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式的 URL。|  
|**-componentsurl=** `location`|設定 Setup.exe 將在其中尋找相依性 (例如 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]) 的 URL。|  
|**-homesite=** `true` **&#124;** `false`|當`true`，從廠商網站上的偏好位置下載的相依性。 這會覆寫 **-componentsurl**設定。 當`false`，從所指定的 URL 下載的相依性 **-componentsurl**。|  
  
## <a name="operating-system-support"></a>作業系統支援  
 Windows Server 2008 Server Core 或 Windows Server 2008 R2 Server Core 提供具有有限功能的低維護伺服器環境，因此不支援 Visual Studio 啟動載入器。 例如，Server Core 安裝選項只支援 .NET Framework 3.5 Server Core 設定檔，因此無法執行與完整 .NET Framework 相依的 Visual Studio 功能。  
  
## <a name="see-also"></a>另請參閱  
 [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)
