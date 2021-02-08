---
title: 應用程式部署必要條件 |Microsoft Docs
description: 瞭解應用程式的部署必要條件，包括使用 [必要條件] 對話方塊和啟動載入器套件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fe8312a4dcaa2efb0b783e89540e5ff9f71f15e6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837797"
---
# <a name="application-deployment-prerequisites"></a>應用程式部署必要條件

若要讓您的應用程式順利安裝並執行，請先安裝應用程式相依于目的電腦的所有元件。 例如，使用建立的大部分應用程式 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 都有 .NET Framework 的相依性。 在此情況下，在安裝應用程式之前，目的地電腦上必須有正確的 common language runtime 版本。

 您可以在 [ **必要條件] 對話方塊** 中選取這些必要條件，然後在安裝過程中安裝 .NET Framework 和任何其他可轉散發套件。 這個做法稱為啟動載入。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]產生名為 *Setup.exe* 的 Windows 可執行程式，也稱為啟動載入 *器。* 啟動載入器負責在應用程式執行前安裝這些必要條件。 如需有關選取這些必要條件的詳細資訊，請參閱 [必要條件對話方塊](../ide/reference/prerequisites-dialog-box.md)。

 每個必要條件都是啟動載入器套件。 啟動載入器套件是一組目錄和檔案，其中包含描述必要條件安裝方式的資訊清單檔。 如果 [必要條件] 對話方塊中未列出您應用程式的必要條件，您可以建立自訂啟動載入器套件並將必要條件新增至 Visual Studio。 然後即可在 [必要條件] 對話方塊中選取必要條件。 如需詳細資訊，請參閱建立啟動載入器 [套件](../deployment/creating-bootstrapper-packages.md)。

 ClickOnce 部署預設會啟用啟動載入。 針對 ClickOnce 部署產生的啟動載入器會經過簽署。 您可以停用元件的啟動載入，但必須確定已在所有目的電腦上安裝正確版本的元件。

## <a name="bootstrapping-and-clickonce-deployment"></a>啟動載入和 ClickOnce 部署
 在用戶端電腦上安裝應用程式之前，請 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 檢查用戶端以確定它具有應用程式資訊清單中指定的需求。 這些包含下列需求：

- Common Language Runtime 的最小必要版本，在應用程式資訊清單中會指定為一個組件相依性。

- 應用程式所需之 Windows 作業系統的最小必要版本，如應用程式資訊清單中的 `<osVersionInfo>` 項目所指定。  (請參閱[ \<dependency> 元素](../deployment/dependency-element-clickonce-application.md)。 ) 

- 必須預先安裝在全域組件快取 (GAC) 的所有元件的最小版本，如組件資訊清單中的元件相依性宣告所指定。

  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 可以偵測到遺漏的必要條件，而且您可以使用啟動載入器來安裝必要條件。 如需詳細資訊，請參閱 [如何：使用 ClickOnce 應用程式安裝必要條件](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)。

> [!NOTE]
> 若要變更 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和 *MageUI.exe* 等工具所產生資訊清單中的值，您必須在文字編輯器中編輯應用程式資訊清單，然後重新簽署應用程式資訊清單和部署資訊清單。 如需詳細資訊，請參閱[如何：重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。

 如果您使用 Visual Studio 和 ClickOnce 部署應用程式，預設會根據方案中的 .NET Framework 版本來選取啟動載入器套件。 但是，如果您變更目標 .NET Framework 版本，則必須手動更新 [必要條件] 對話方塊中的選項。

|目標 .NET Framework|選取的啟動載入器套件|
|---------------------------|------------------------------------|
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|

 使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署時，由 [[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 發行精靈] 所產生的 *Publish.htm* 網頁會指向只安裝應用程式的連結，或是指向同時安裝應用程式和啟動載入元件的連結。

 如果您使用 [ClickOnce 發行嚮導] 或 Visual Studio 中的 [發行] 頁面產生啟動載入器，則會自動簽署 *Setup.exe* 。 但是，如果您要使用客戶的憑證來簽署啟動載入器，則可以稍後再簽署這個檔案。

## <a name="bootstrapping-and-msbuild"></a>啟動載入和 MSBuild
 如果您不使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，而是在命令列上編譯您的應用程式，您可以 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用 Microsoft Build Engine (MSBuild) 工作來建立啟動載入應用程式。 如需詳細資訊，請參閱 [GenerateBootstrapper task](../msbuild/generatebootstrapper-task.md)。

 您也可以使用電子軟體散發系統 (例如 Microsoft Systems Management Server (SMS)) 來預先部署元件，而不使用啟動載入。

## <a name="bootstrapper-setupexe-command-line-arguments"></a>啟動載入器 (Setup.exe) 命令列引數
 和 MSBuild 工作所產生的 *Setup.exe* [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 支援下列一組命令列引數。 任何其他引數都會轉送至應用程式安裝程式。

 如果您變更任何啟動載入器選項，則必須變更未簽署的啟動載入器，稍後再簽署啟動載入器檔案。

| 命令列引數 | Description |
| - | - |
| **-?, -h, -help** | 顯示 [說明] 對話方塊。 |
| **-url, -componentsurl** | 顯示此安裝程式的儲存 URL 和元件 URL。 |
| **-url =**`location` | 設定 *Setup.exe* 將在其中尋找 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的 URL。 |
| **-componentsurl=** `location` | 設定 *Setup.exe* 將在其中尋找相依性的 URL，例如 .NET Framework。 |
| **-homesite=** `true` **&#124;** `false` | 當為時 `true` ，會從廠商網站上的慣用位置下載相依性。 此設定會覆寫 **-componentsurl** 設定。 當為時 `false` ，從 **-componentsurl** 指定的 URL 下載相依性。 |

## <a name="operating-system-support"></a>作業系統支援
 Windows Server 2008 Server Core 或 Windows Server 2008 R2 Server Core 上不支援 Visual Studio 啟動載入器，因為它們提供有限功能的低維護伺服器環境。 例如，Server Core 安裝選項僅支援 .NET Framework 3.5 Server Core 設定檔，而該設定檔無法執行相依于完整 .NET Framework 的 Visual Studio 功能。

## <a name="see-also"></a>另請參閱
- [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)