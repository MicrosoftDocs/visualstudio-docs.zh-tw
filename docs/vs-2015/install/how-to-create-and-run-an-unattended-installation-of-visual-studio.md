---
title: 如何：建立和執行自動安裝 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- installing Visual Studio, unattended
- unattended installation, Visual Studio
ms.assetid: 3867b5dc-ed34-4ee2-be32-a42e7e320517
caps.latest.revision: 44
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 26e059d4fdc8eadd422924dd6bbda6f7c945ccfb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839225"
---
# <a name="how-to-create-and-run-an-unattended-installation-of-visual-studio"></a>How to: Create and Run an Unattended Installation of Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以透過內部網路上的自動執行安裝 (也就是自訂的無訊息安裝)，而不是從媒體 (例如 DVD) 安裝的方式，執行 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 安裝應用程式。 本主題說明如何準備 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，以便從網路共用進行此類型的安裝。

## <a name="creating-a-network-image"></a>建立網路映像
 首先，建立 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 媒體的網路映像。

#### <a name="to-create-a-network-image"></a>建立網路映像

1. 在伺服器上建立資料夾 (例如：<磁碟機>**:\IDEinstall\\)。

2. 從 [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) 下載安裝程式，然後執行<產品>**.exe /Layout <磁碟機>**:\IDEinstall\

3. 在網路上共用 IDEinstall 資料夾，然後設定適當的安全性設定。

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的安裝應用程式網路路徑類似 \\\\<伺服器名稱>** \IDEinstall\\<產品>**.exe。

    > [!NOTE]
    > 如果任何路徑與檔名的組合超過 260 個字元，則安裝可能會失敗。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 路徑的長度上限為 221 個字元。  本機路徑名稱不應超過 70 個字元，且網路路徑名稱不應超過 39 個字元。

     如果路徑中的資料夾名稱包含內嵌空格 (例如 " \\ \\ *servername*common7\ide\privateassemblies install" 或 \\ \\ *servername*\Visual Studio \\) ，安裝也會失敗。

## <a name="deploying-visual-studio-in-unattended-mode"></a>以自動模式部署 Visual Studio
 若要以自動模式部署 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，您必須修改 AdminDeployment.xml 檔案。 若要這樣做，您必須先使用 `/CreateAdminFile` *\<file location>* 命令列參數建立 AdminDeployment.xml 檔案。 如果您將檔案放在 *磁碟機*:\IDEinstall\packages 目錄，即可使用此檔案將 Visual Studio 部署推送至您的網路或提取至安裝中。 AdminDeployment.xml 檔案對於作業系統、架構、Visual Studio 版本或作業系統語言不是唯一的。

> [!CAUTION]
> 有時，無法安裝 AdminDeployment.xml 檔案中列為選取的項目。 若要解決這個問題，請將標記為 “Selected="是"” 的項目放在 AdminDeployment.xml 檔案的 **結尾處** 。
>
> 如果不想安裝項目的選擇性相依性，則必須先選取父代，再取消選取父代後的選擇性相依性，如下列螢幕擷取畫面所示：
>
> ![AdminDeployment.xml 檔案結尾處的安裝項目](../install/media/vs2015-install-endoffileadmindeploy.PNG "vs2015_Install_EndOfFileAdminDeploy")
>
> 執行這項作業的另一個方法，就是省略父代的選擇性子系，換言之，不包括任何 “Selected=”否”” 的項目；但是您仍然必須將所有 “Selected=”是”” 的項目放在 AdminDeployment.xml 檔案的結尾處。

> [!IMPORTANT]
> 進行安裝時，電腦可能會自動重新啟動一次或多次。 重新啟動之後，您必須使用在執行安裝且電腦重新啟動前所用的相同使用者登入帳戶來重新登入。 您可以在執行自動安裝之前先安裝必要條件元件，即可避免自動重新啟動。 如需詳細資訊，請參閱 [Visual Studio Administrator Guide](../install/visual-studio-administrator-guide.md)中的＜避免設定期間重新啟動＞一節。

 AdminDeployment 檔案結構描述包含下列項目：

|項目|屬性|值|描述|
|-------------|---------------|------------|-----------------|
|BundleCustomizations|TargetDir|*路徑*|運作方式與覆寫安裝應用程式使用者介面中的路徑相同。 如果 Visual Studio 中已安裝，則會略過此項目。|
|BundleCustomizations|NoWeb|是&#124;預設值|如果項目的值為 yes，則安裝應用程式不會嘗試在安裝動作時移至 Web。|
|SelectableItemCustomization|Hidden|是&#124;否|如果項目的值為 Yes，則會隱藏自訂樹狀結構中的可選取項目。|
|SelectableItemCustomization|已選取|是&#124;否|選取或清除自訂樹狀結構中的可選取項目。|
|BundleCustomizations|摘要|Path|使用者想要使用的摘要位置。  此摘要用於電腦上的後續修改作業 (預設為 "Default")。|
|BundleCustomizations|SuppressRefreshPrompt|是&#124;預設值|如果有可用的較新版本，會避免使用者看到重新整理安裝程式的提示。|
|BundleCustomizations|NoRefresh|是&#124;預設值|如果有可用的較新版本，不會重新整理安裝程式。|
|BundleCustomizations|NoCacheOnlyMode|是&#124;預設值|防止封裝快取的預先填入。|

> [!WARNING]
> 安裝應用程式將會接受 SelectableItem 的 Selected 狀態，即使它是隱藏的。 例如，如果您想要一律安裝可選取的項目，可以將其標記為隱藏和已選取。

#### <a name="to-create-an-unattended-installation-of-visual-studio"></a>若要建立和執行自動 Visual Studio 安裝程式

1. 在 *磁碟機*:\IDEinstall\AdminDeployment.xml 檔案中，將 BundleCustomizations 項目的 NoWeb 屬性值從 "default" 變更為 "yes"，如下列範例所示：

     將 `<BundleCustomizations TargetDir="default" NoWeb="default"/>` 變更為 `<BundleCustomizations TargetDir="default" NoWeb="yes"/>`

2. 視需要變更選擇性元件的 SelectableItemCustomization 屬性，然後儲存檔案。

## <a name="running-unattended-setup"></a>執行自動安裝
 您可以透過在用戶端電腦上自動執行 Visual Studio 安裝應用程式，或允許使用者使用您所定義之設定執行應用程式本身的方式，來執行自動安裝。

#### <a name="to-run-an-unattended-installation-on-a-client-computer"></a>在用戶端電腦上執行自動安裝

- 開啟 [開始]**** 功能表，選擇 [執行]****，然後輸入 \\\\<伺服器名稱>** \IDEinstall\vs_<產品>**.exe /adminfile *PathOfTheAdmindeployment.xmlFile*<em>AdditionalParametersAsNeeded</em>

   例如，您可以指定下列命令列：`\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\ IDEinstall\AdminDeployment.xml /quiet /norestart`

#### <a name="to-enable-clients-to-manually-install-visual-studio-with-pre-defined-settings"></a>讓用戶端以預先定義的設定手動安裝 Visual Studio

1. 將自訂的 AdminDeployment.xml 檔案複製到唯讀的網路共用 (例如：<伺服器名稱>\\\\** \IDEinstall\packages\AdminDeployment.xml)。

2. 讓使用者從該共用進行安裝。

## <a name="maintaining-an-installation"></a>維護安裝
 如果您開啟 [控制台] **** 然後重新安裝應用程式，您可以修改 Visual Studio 功能，解除安裝程式語言和修復或解除安裝 Visual Studio。

> [!NOTE]
> 您必須具有本機電腦上的系統管理認證，才可以使用維護模式。

#### <a name="to-maintain-an-installation-on-a-client-computer"></a>維護用戶端電腦上的安裝

- 開啟 [控制台] ****，然後選擇 [程式和功能] ****。

- 選擇 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，然後選擇 [變更] ****。

#### <a name="to-change-admindeployment-settings-on-a-client-computer-after-visual-studio-has-been-installed"></a>在 Visual Studio 安裝之後變更在用戶端電腦上的 AdminDeployment 設定

1. 視需要更新 AdminDeployment.xml。

2. 開啟 [開始] **** 功能表，然後選擇 [執行] ****。

3. 輸入下列文字：\\\\<伺服器名稱>** \IDEinstall\vs_<產品>**.exe /AdminFile PathToAdmindeployment.xml 檔案

    AdditionalParametersAsNeeded

    例如，您可以指定下列命令列：`\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\IDEinstall\AdminDeployment.xml /quiet /norestart`

   安裝 Visual Studio 之後，Repair 是預設參數。 如果您使用更新的 /AdminFile 來修復 Visual Studio，將會以更新後的 AdminDeployment.xml 檔案所叫用的設定，來覆寫最新的管理部署設定。

## <a name="updating-an-installation"></a>更新安裝
 Microsoft 已發行數個 Visual Studio 2015 更新。 本節說明如何更新 Visual Studio 2015 的自動安裝映像，使其包含更新。

#### <a name="to-update-an-unattended-installation-of-visual-studio"></a>更新 Visual Studio 自動安裝

1. 找到現有網路映像中的 <產品>.exe 檔案，按一下滑鼠右鍵，然後按一下 [屬性]****。

2. 按一下 [詳細資料]**** 索引標籤，然後記下 [產品版本]**** 屬性。

    ![Visual Studio 自動安裝中的 [屬性] 對話方塊範例](../install/media/unattended-install-properties-dialog-box.PNG "自動安裝-[屬性] 對話方塊")

3. ###### <a name="if-the-product-version-is-140247200-or-140247201-follow-these-steps"></a>如果產品版本為 14.0.24720.0 或 14.0.24720.1，請遵循下列步驟：
   1. 在可存取網際網路的電腦上，執行 <產品>.exe** /Layout <磁碟機:** \IDEinstall。 (例如，執行：`vs_enterprise.exe /Layout d:\IDEinstall`。)

   2. 在 /Layout 完成之後，請將新的映像複製到新位置。

   3. 建立和修改 AdminDeployment.xml 檔案。 若要這樣做，請使用 `/CreateAdminFile` *\<file location>* 命令列參數。 (如需詳細資訊，請參閱本文的「以自動模式部署 Visual Studio」一節。)

   4. 在用戶端電腦上，執行下列命令以更新您先前安裝的 Visual Studio 的複本："\\\\*server1*\IDEinstall_Updated_1\\<產品>.exe** /adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml/quiet/norestart"。

        例如，執行：`\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`
5. ###### <a name="for-other-product-version-values-follow-these-steps"></a>如需其他產品版本值，請依照下列步驟進行：
   1. 在可存取網際網路的電腦上，執行 <產品>.exe** /Layout <磁碟機:** \IDEinstall。 (例如，執行 `vs-enterprise.exe /Layout d:\IDEinstall`。)

   2. 在 /Layout 完成之後，請將新的映像複製到新位置。 (或，您可以改為覆寫現有網路映像。)

   3. 建立 AdminDeployment.xml 檔案，然後予以修改。 若要這樣做，請使用 `/CreateAdminFile` *\<file location>* 命令列參數。 (如需詳細資訊，請參閱本文的「以自動模式部署 Visual Studio」一節。)

   4. 如果您將映像複製到新位置時，您必須在用戶端電腦上執行下列命令，以更新您先前安裝的 Visual Studio 複本："\\\\*server1*\IDEinstall_Updated_1\\<產品>.exe** /adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart"。

        例如，執行：`\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`

   5. 如果您覆寫現有的網路映像，您可以執行上一個步驟中所列的命令，或您可以執行下列動作：
       1. 開啟 [控制台] ****，然後選擇 [程式和功能] ****。

       2. 選擇 [Visual Studio]****，然後選擇 [變更]****。

       3. 在 Visual Studio 以維護模式啟動之後，按一下 [修改]****。

       4. [功能] 頁面上應該會出現最新的更新。 選取您想要安裝的其他功能，請按 [下一步]****，然後按一下 [更新]**** 以安裝更新和新功能。

## <a name="registering-the-product"></a>註冊產品
 安裝完成之後，即可從 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 內註冊您的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]複本。

#### <a name="to-register"></a>進行註冊

1. 開啟 [說明] **** 功能表，然後選擇 [註冊產品] ****。

2. 輸入產品金鑰。

     (如需詳細資訊，請參閱[如何：找出 Visual Studio 產品金鑰](../install/how-to-locate-the-visual-studio-product-key.md)與[如何：在部署 Visual Studio 時自動套用產品金鑰](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md)主題。)

## <a name="see-also"></a>另請參閱
 [安裝 Visual Studio](../install/install-visual-studio-2015.md)