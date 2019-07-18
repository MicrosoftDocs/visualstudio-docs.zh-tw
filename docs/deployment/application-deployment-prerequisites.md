---
title: 應用程式部署必要條件 |Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8206e199acc3ccb76cf89603d48bed0173129218
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746065"
---
# <a name="application-deployment-prerequisites"></a>應用程式部署必要條件

若要順利安裝及執行您應用程式，請先安裝您的應用程式是相依到目標電腦上的所有元件。 例如，大部分的應用程式使用建立[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]有相依性 .NET Framework。 在此情況下，通用語言執行平台的正確版本必須先存在於目的地電腦上已安裝的應用程式。

 您可以選取這些先決條件**Prerequisites Dialog Box**和安裝.NET Framework，以及任何其他可轉散發套件安裝的一部分。 這個做法稱為啟動載入  。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會產生名為 Windows 可執行程式*Setup.exe*也稱為*啟動載入器*。 啟動載入器負責在應用程式執行前安裝這些必要條件。 如需有關如何選取這些必要條件的詳細資訊，請參閱 <<c0> [ 必要條件對話方塊](../ide/reference/prerequisites-dialog-box.md)。

 每個必要條件都是啟動載入器套件。 啟動載入器套件是一組目錄和內含描述必要條件的安裝方式的資訊清單檔案的檔案。 如果 [必要條件]  對話方塊中未列出您應用程式的必要條件，您可以建立自訂啟動載入器套件並將必要條件新增至 Visual Studio。 然後即可在 [必要條件]  對話方塊中選取必要條件。 如需詳細資訊，請參閱 <<c0> [ 建立啟動載入器套件](../deployment/creating-bootstrapper-packages.md)。

 ClickOnce 部署預設會啟用啟動載入。 針對 ClickOnce 部署產生的啟動載入器會經過簽署。 您可以停用的元件，啟動程序，但只有當確定所有目標電腦上已安裝正確版本的元件。

## <a name="bootstrapping-and-clickonce-deployment"></a>啟動載入和 ClickOnce 部署
 用戶端電腦上安裝應用程式之前[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]會檢查以確定它具有應用程式資訊清單中指定之需求的用戶端。 這些包括下列需求：

- Common Language Runtime 的最小必要版本，在應用程式資訊清單中會指定為一個組件相依性。

- 應用程式所需之 Windows 作業系統的最小必要版本，如應用程式資訊清單中的 `<osVersionInfo>` 項目所指定。 (請參閱[\<相依性 > 項目](../deployment/dependency-element-clickonce-application.md)。)

- 必須預先安裝在全域組件快取 (GAC) 中，組件資訊清單中的組件相依性宣告所指定的所有組件的最小版本。

  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 可以偵測遺漏的必要條件，然後您可以使用啟動載入器，以便安裝必要條件。 如需詳細資訊，請參閱[如何：隨著 ClickOnce 應用程式安裝必要軟體](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)。

> [!NOTE]
> 若要變更 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和 *MageUI.exe* 等工具所產生資訊清單中的值，您必須在文字編輯器中編輯應用程式資訊清單，然後重新簽署應用程式資訊清單和部署資訊清單。 如需詳細資訊，請參閱[如何：重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。

 如果您使用 Visual Studio 和 ClickOnce 部署應用程式，預設會根據方案中的 .NET Framework 版本來選取啟動載入器套件。 但是，如果您變更目標 .NET Framework 版本，則必須手動更新 [必要條件]  對話方塊中的選項。

|目標 .NET Framework|選取的啟動載入器套件|
|---------------------------|------------------------------------|
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|

 使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署時，由 [[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 發行精靈] 所產生的 *Publish.htm* 網頁會指向只安裝應用程式的連結，或是指向同時安裝應用程式和啟動載入元件的連結。

 如果您使用 [ClickOnce 發行精靈] 或 Visual Studio 中的 [發行] 頁面產生啟動載入器，將會自動簽署 *Setup.exe*。 但是，如果您要使用客戶的憑證來簽署啟動載入器，則可以稍後再簽署這個檔案。

## <a name="bootstrapping-and-msbuild"></a>啟動載入和 MSBuild
 如果您不要使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，但而不是編譯您的應用程式，在命令列上，您可以建立[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]啟動載入應用程式，藉由使用 Microsoft Build Engine (MSBuild) 工作。 如需詳細資訊，請參閱 < [GenerateBootstrapper 工作](../msbuild/generatebootstrapper-task.md)。

 您也可以使用電子軟體散發系統 (例如 Microsoft Systems Management Server (SMS)) 來預先部署元件，而不使用啟動載入。

## <a name="bootstrapper-setupexe-command-line-arguments"></a>啟動載入器 (Setup.exe) 命令列引數
 *Setup.exe*所產生[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和 MSBuild 工作支援下列的命令列引數集。 任何其他引數會轉送給應用程式安裝程式。

 如果您變更任何啟動載入器的選項，您就必須變更不帶正負號的啟動載入器，然後稍後再簽署啟動載入器檔案。

| 命令列引數 | 描述 |
| - | - |
| **-?, -h, -help** | 顯示 [說明] 對話方塊。 |
| **-url, -componentsurl** | 顯示此安裝程式的儲存 URL 和元件 URL。 |
| **-url=** `location` | 設定 *Setup.exe* 將在其中尋找 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的 URL。 |
| **-componentsurl=** `location` | 設定 URL，其中*Setup.exe*會尋找相依性，例如.NET Framework。 |
| **-homesite=** `true` **&#124;** `false` | 當`true`，從廠商網站上的偏好位置下載的相依性。 此設定會覆寫 **-componentsurl**設定。 當`false`，從所指定的 URL 下載的相依性 **-componentsurl**。 |

## <a name="operating-system-support"></a>作業系統支援
 Visual Studio 啟動載入器不支援在 Windows Server 2008 Server Core 或 Windows Server 2008 R2 Server Core，因為它們提供的低維護伺服器環境，但功能受限。 例如，Server Core 安裝選項僅支援.NET Framework 3.5 Server Core 設定檔，無法執行相依於完整.NET Framework 的 Visual Studio 功能。

## <a name="see-also"></a>另請參閱
- [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)