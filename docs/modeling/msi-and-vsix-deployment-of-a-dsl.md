---
title: DSL 的 MSI 和 VSIX 部署
description: 瞭解如何在您自己的電腦或其他電腦上安裝特定領域語言 (DSL) 。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bf6082ec8860f7f50e758eb65a8471ece94103aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950407"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>DSL 的 MSI 和 VSIX 部署
您可以在自己的電腦或其他電腦上安裝特定領域語言。 必須已在目的電腦上安裝 Visual Studio。

## <a name="choosing-between-vsix-and-msi-deployment"></a><a name="which"></a> 在 VSIX 與 MSI 部署之間進行選擇
 部署特定領域語言的方法有兩種：

|方法|優點|
|-|-|
|VSX (Visual Studio 延伸模組) |很容易部署：從 DslPackage 專案複製並執行 **.vsix** 檔案。<br /><br /> 如需詳細資訊，請參閱 [使用 VSX 安裝和卸載 DSL](#Installing)。|
|MSI (安裝程式檔案) |-允許使用者按兩下 DSL 檔案以開啟 Visual Studio。<br />-將圖示與目的電腦中的 DSL 檔案類型產生關聯。<br />-將 XSD (XML 架構) 與 DSL 檔案類型產生關聯。 這可避免在將檔案載入 Visual Studio 時發生警告。<br /><br /> 您必須將安裝專案加入至您的方案，才能建立 MSI。<br /><br /> 如需詳細資訊，請參閱 [使用 MSI 檔案部署 DSL](#msi)。|

## <a name="install-and-uninstall-a-dsl-by-using-the-vsx"></a><a name="Installing"></a> 使用 VSX 安裝和卸載 DSL

當您的 DSL 是透過此方法安裝時，使用者可以從 Visual Studio 中開啟 DSL 檔案，但無法從 Windows 檔案總管開啟該檔案。

### <a name="to-install-a-dsl-by-using-the-vsx"></a>使用 VSX 安裝 DSL

1. 找出您的 DSL 封裝專案所建立的 **.vsix** 檔案：

   1. 在 **方案總管** 中，以滑鼠右鍵按一下 **DslPackage** 專案，然後按一下 [ **開啟資料夾] 檔案總管**。

   2. 找出檔案 **bin \\ \* \\** _yourproject。_**。DslPackage .vsix**

2. 將 **.vsix** 檔複製到您要安裝 DSL 的目的電腦上。 這可以是您自己的電腦或其他電腦。

   - 目的電腦必須具有在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 執行時間支援 dsl 的其中一個版本。 如需詳細資訊，請參閱 [Visual Studio 的視覺效果 & 模型 SDK 支援版本](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)。

   - 目的電腦必須具有 **DslPackage\source.extensions.manifest** 中所指定的其中一個版本的 Visual Studio。

3. 在目的電腦上，按兩下 **.vsix** 檔案。

    [Visual Studio 擴充功能安裝程式] 會隨即開啟並安裝擴充功能。

4. 啟動或重新啟動 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]。

5. 若要測試 DSL，請使用 Visual Studio 建立具有您為 DSL 定義之副檔名的新檔案。

### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>卸載使用 VSX 安裝的 DSL

1. 在 [ **工具** ] 功能表中選擇 [ **擴充功能和更新**]。

2. 展開 [已安裝的擴充功能] 。

3. 選取用來定義 DSL 的延伸模組，然後按一下 [ **卸載**]。

   在很少見的情況下，錯誤的擴充功能會無法載入，並且在錯誤視窗中建立報表，但不會顯示在擴充管理員中。 在此情況下，您可以藉由從下列位置刪除檔案來移除擴充功能：

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="deploying-a-dsl-in-an-msi"></a><a name="msi"></a> 在 MSI 中部署 DSL
 藉由為您的 DSL 定義 MSI (Windows Installer) 檔案，您可以允許使用者從 Windows 檔案總管開啟 DSL 檔案。 您也可以將圖示和簡短描述與副檔名產生關聯。 此外，MSI 還可以安裝可用於驗證 DSL 檔案的 XSD。 如果您想要的話，也可以將其他元件新增至要同時安裝的 MSI。

 如需有關 MSI 檔案和其他部署選項的詳細資訊，請參閱 [部署應用程式、服務和元件](../deployment/deploying-applications-services-and-components.md)。

 若要建立 MSI，請將安裝專案新增至您的 Visual Studio 方案。 建立安裝專案最簡單的方法是使用 CreateMsiSetupProject.tt 範本，您可以從 [VMSDK 網站](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)下載該範本。

### <a name="to-deploy-a-dsl-in-an-msi"></a>在 MSI 中部署 DSL

1. `InstalledByMsi`在延伸模組資訊清單中設定。 這可防止在 MSI 以外安裝和卸載 VSX。 如果您將在 MSI 中包含其他元件，這就很重要。

   1. 開啟 DslPackage\source.extension.tt

   2. 在前面插入下行 `<SupportedProducts>` ：

       ```xml
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. 建立或編輯將在 Windows 檔案總管中代表 DSL 的圖示。 例如，編輯 **DslPackage\Resources\File.ico**

3. 請確定 DSL 的下列屬性是正確的：

   - 在 [DSL Explorer] 中，按一下根節點，然後在屬性視窗中，查看：

       - 描述

       - 版本

   - 按一下 [ **編輯器** ] 節點，然後在 [屬性視窗中，按一下 [ **圖示**]。 設定值以參考 **DslPackage\Resources** 中的圖示檔，例如 **file .ico**

   - 在 [ **組建** ] 功能表上，開啟 [ **設定管理員**]，然後選取您想要建立的設定，例如 [ **發行** ] 或 [ **調試** 程式]。

4. 移至 [視覺效果和模型 SDK 首頁](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)，然後從 [ **下載** ] 索引標籤下載 **CreateMsiSetupProject.tt**。

5. 將 **CreateMsiSetupProject.tt** 新增至您的 Dsl 專案。

    Visual Studio 將會建立名為 **CreateMsiSetupProject. vdproj** 的檔案。

6. 在 Windows 檔案總管中，將 Dsl \\ *. vdproj 複製到名為 Setup 的新資料夾。

     (您想要的話，您現在可以從 Dsl 專案中排除 CreateMsiSetupProject.tt。 ) 

7. 在 **方案總管** 中，**將 \\ \* vdproj** 新增為現有的專案。

8. 在 [ **專案** ] 功能表上，按一下 [專案相依性 **]**。

    在 [ **專案** 相依性] 對話方塊中，選取 [安裝] 專案。

    選取 [ **DslPackage**] 旁的方塊。

9. 重建方案。

10. 在 Windows 檔案總管中，于安裝專案中找出內建的 MSI 檔案。

     將 MSI 檔案複製到您要安裝 DSL 的電腦。 按兩下 MSI 檔案。 執行安裝程式。

11. 在目的電腦中，建立具有 DSL 副檔名的新檔案。 驗證：

    - 在 Windows 檔案總管清單視圖中，檔案會以您定義的圖示和描述顯示。

    - 當您按兩下檔案時，Visual Studio 會啟動，並在您的 DSL 編輯器中開啟 DSL 檔案。

    如果您想要的話，也可以手動建立安裝專案，而不是使用文字模板。 如需包含此程式的逐步解說，請參閱 [視覺效果和模型化 SDK 實驗室](https://code.msdn.microsoft.com/DSLToolsLab/Release/ProjectReleases.aspx?ReleaseId=4207)的第5章。

### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>卸載從 MSI 安裝的 DSL

1. 在 Windows 中，開啟 [ **程式和功能** ] 控制台。

2. 卸載 DSL。

3. 重新啟動 Visual Studio。
