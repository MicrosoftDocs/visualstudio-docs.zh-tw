---
title: Visual Studio 系統管理員指南
titleSuffix: ''
description: 深入了解如何在企業環境中部署 Visual Studio。
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ba41c545c2af2e0490ef0410fde7849706123940
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306705"
---
# <a name="visual-studio-administrator-guide"></a>Visual Studio 系統管理員指南

在企業環境中，系統管理員通常會從網路共用或使用系統管理軟體，將安裝部署給終端使用者。 我們已設計 Visual Studio 安裝程式引擎來支援企業部署，讓系統管理員可以建立網路安裝位置、預先設定安裝預設、在安裝程序期間部署產品金鑰，以及在成功推出後管理產品更新。

此系統管理員指南針對網路環境中的企業部署，提供以案例為基礎的指導方針。

## <a name="before-you-begin"></a>開始之前

為整個組織部署 Visual Studio 之前，有幾個要制訂之決策和完成的工作：

::: moniker range=">=vs-2019"

* 確認每部目標電腦都符合[基本安裝需求](/visualstudio/releases/2019/system-requirements/)。

::: moniker-end

::: moniker range="vs-2017"

* 確認每部目標電腦都符合[基本安裝需求](/visualstudio/productinfo/vs2017-system-requirements-vs/)。

::: moniker-end

* 決定您的服務需求。

  如果您的公司需要長時間使用功能集，但仍想要取得服務的定期更新，請計劃使用服務基準。 For more information, see the ***Support options for Enterprise and Professional customers*** section of the [Visual Studio product lifecycle and servicing](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers) page, as well as the [Update Visual Studio while on a servicing baseline](update-servicing-baseline.md) page.

* 決定更新模型。

  您要讓個別用戶端電腦從中取得產品更新的位置？ 具體而言，請決定是否要讓用戶端從網際網路或全公司的本機共用取得更新。 接著，如果您選擇使用本機的共用，請決定要由個別使用者更新自己的用戶端，或由系統管理員以程式設計方式更新用戶端。 最好是在用戶端電腦上執行原始安裝之前做出這些決策。 如需詳細資訊，請參閱[建立 Visual Studio 的網路型安裝](../install/create-a-network-installation-of-visual-studio.md)。

  您可以使用最新的產品更新來更新 Visual Studio 的網路安裝配置，使其可作為最新的 Visual Studio 更新的安裝點，也能維護已部署至用戶端工作站的安裝。 如需詳細資訊，請參閱 [更新以網路為基礎的 Visual Studio 安裝](../install/update-a-network-installation-of-visual-studio.md)。

  利用企業部署工具的組織可以利用 Microsoft Update 目錄和 Windows Server Update Services 上 Visual Studio 更新的事實。 如需詳細資訊，請參閱 [啟用系統管理員更新](../install/enabling-administrator-updates.md) 和套用 [系統管理員更新](../install/applying-administrator-updates.md)。

  針對未連線到網際網路的電腦，建立最基本的版面配置是更新離線 Visual Studio 實例的最簡單且最快速的方式。 如需詳細資訊，請參閱 [使用基本的離線配置來更新 Visual Studio](update-minimal-layout.md)。

::: moniker range=">=vs-2019"

* 決定您公司需要的[工作負載和元件](workload-and-component-ids.md?view=vs-2019&preserve-view=true)。

* 決定是否要使用[回應檔案](automated-installation-with-response-file.md?view=vs-2019&preserve-view=true) (可簡化指令碼檔案中的詳細資料管理作業)。

::: moniker-end

::: moniker range="vs-2017"

* 決定您公司需要的[工作負載和元件](workload-and-component-ids.md?view=vs-2017&preserve-view=true)。

* 決定是否要使用[回應檔案](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true) (可簡化指令碼檔案中的詳細資料管理作業)。

::: moniker-end

* 決定要啟用群組原則，還是要將 Visual Studio 設定為停用個別電腦上的客戶回函。

::: moniker range=">=vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>步驟 1 - 下載 Visual Studio 產品檔案

* [選取您想要安裝的工作負載和元件](workload-and-component-ids.md?view=vs-2019&preserve-view=true)。

* [建立 Visual Studio 產品檔案的網路共用](create-a-network-installation-of-visual-studio.md?view=vs-2019&preserve-view=true)。

## <a name="step-2---build-an-installation-script"></a>步驟 2 - 建置安裝指令碼

* 建置使用[命令列參數](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true)的安裝指令碼以控制安裝。

  >[!NOTE]
  > 您可以使用[回應檔案](automated-installation-with-response-file.md?view=vs-2019&preserve-view=true)來簡化指令碼。 請務必建立包含預設安裝選項的回應檔案。

* (選擇性) 在執行安裝指令碼時[套用大量授權產品金鑰](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019&preserve-view=true)，以讓使用者不需要另行啟用軟體。

* (選擇性) 更新網路配置以[控制產品更新傳遞至終端使用者的時間和來源位置](controlling-updates-to-visual-studio-deployments.md?view=vs-2019&preserve-view=true)。

* (選擇性) 設定會影響 Visual Studio 部署的登錄原則，例如要與其他版本或執行個體共用之部分套件的安裝位置、[快取套件的位置](set-defaults-for-enterprise-deployments.md?view=vs-2019&preserve-view=true)或[是否要快取套件](disable-or-move-the-package-cache.md?view=vs-2019&preserve-view=true)。

* (選擇性) 設定群組原則。 您也可以[將 Visual Studio 設定為停用個別電腦上的客戶意見反應](../ide/visual-studio-experience-improvement-program.md)。

## <a name="step-3---deploy-updates"></a>步驟 3-部署更新

使用選擇的部署技術，在目標開發人員工作站上執行指令碼。

* 定期執行您在步驟1中所使用的命令來新增更新的元件，以[更新您的網路位置，並提供](update-a-network-installation-of-visual-studio.md?view=vs-2019&preserve-view=true)Visual Studio 的最新更新。

  您可以使用更新指令碼來更新 Visual Studio。 若要這樣做，請使用 [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) 命令列參數。

  您可以使用 System Center 設定管理員等工具，從 Windows Server Update Services 或 Microsoft Update 類別目錄部署 Visual Studio 更新。  如需詳細資訊，請參閱套用 [系統管理員更新](applying-administrator-updates.md) 。 

## <a name="step-4---optional-use-visual-studio-tools-to-verify-installation"></a>步驟 4- (選用) 使用 Visual Studio 工具來確認安裝

我們提供數種工具來協助您[偵測和管理用戶端電腦上已安裝的 Visual Studio 執行個體](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true)。

## <a name="advanced-configuration"></a>進階組態

根據預設，Visual Studio 安裝可讓您從錯誤清單 F1 和程式碼連結，在 Bing 搜尋中包含自訂類型。 您可以藉由依原則變更下列登錄機碼的值，將 Visual Studio 設定為停用搜尋機制，使其不包含任何自訂使用者類型：

**"PutCustomTypeInBingSearch" DWORD 0**

登錄位於您私用登錄區的 * Software\Microsoft\VisualStudio\16.0_ {InstanceId} \ Roslyn\Internal\Diagnostics \* 目錄中。 如需如何開啟登錄 hive 的指示，請參閱 [編輯 Visual Studio 實例的](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true#editing-the-registry-for-a-visual-studio-instance)登錄。

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>步驟 1 - 下載 Visual Studio 產品檔案

* [選取您想要安裝的工作負載和元件](workload-and-component-ids.md?view=vs-2017&preserve-view=true)。

* [建立 Visual Studio 產品檔案的網路共用](create-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true)。

## <a name="step-2---build-an-installation-script"></a>步驟 2 - 建置安裝指令碼

* 建置使用[命令列參數](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017&preserve-view=true)的安裝指令碼以控制安裝。

  >[!NOTE]
  > 您可以使用[回應檔案](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true)來簡化指令碼。 請務必建立包含預設安裝選項的回應檔案。

* (選擇性) 在執行安裝指令碼時[套用大量授權產品金鑰](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017&preserve-view=true)，以讓使用者不需要另行啟用軟體。

* (選擇性) 更新網路配置以[控制產品更新傳遞至終端使用者的時間和來源位置](controlling-updates-to-visual-studio-deployments.md?view=vs-2017&preserve-view=true)。

* (選擇性) 設定會影響 Visual Studio 部署的登錄原則，例如要與其他版本或執行個體共用之部分套件的安裝位置、[快取套件的位置](set-defaults-for-enterprise-deployments.md?view=vs-2019&preserve-view=true)或[是否要快取套件](disable-or-move-the-package-cache.md?view=vs-2017&preserve-view=true)。

* (選擇性) 設定群組原則。 您也可以[將 Visual Studio 設定為停用個別電腦上的客戶意見反應](../ide/visual-studio-experience-improvement-program.md)。

## <a name="step-3---deploy-updates"></a>步驟 3-部署更新

使用選擇的部署技術，在目標開發人員工作站上執行指令碼。

* 定期執行您在步驟1中所使用的命令來新增更新的元件，以[更新您的網路位置，並提供](update-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true)Visual Studio 的最新更新。

  您可以使用更新指令碼來更新 Visual Studio。 若要這樣做，請使用 [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) 命令列參數。

  您可以使用 System Center 設定管理員等工具，從 Windows Server Update Services 或 Microsoft Update 類別目錄部署 Visual Studio 更新。 如需詳細資訊，請參閱套用 [系統管理員更新](applying-administrator-updates.md)。

## <a name="step-4---optional-use-visual-studio-tools-to-verify-installation"></a>步驟 4- (選用) 使用 Visual Studio 工具來確認安裝

我們提供數種工具來協助您[偵測和管理用戶端電腦上已安裝的 Visual Studio 執行個體](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true)。

## <a name="advanced-configuration"></a>進階組態

根據預設，Visual Studio 安裝可讓您從錯誤清單 F1 和程式碼連結，在 Bing 搜尋中包含自訂類型。 您可以藉由依原則變更下列登錄機碼的值，將 Visual Studio 設定為停用搜尋機制，使其不包含任何自訂使用者類型：

**"PutCustomTypeInBingSearch" DWORD 0**

登錄位於 `Software\Microsoft\VisualStudio\15.0_{InstanceId}\Roslyn\Internal\Diagnostics\` 您私人登錄 hive 的目錄中。 如需如何開啟登錄 hive 的指示，請參閱 [編輯 Visual Studio 實例的](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true#editing-the-registry-for-a-visual-studio-instance)登錄。

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [啟用系統管理員更新](enabling-administrator-updates.md)
* [套用系統管理員更新](applying-administrator-updates.md)
* [命令列參數範例](command-line-parameter-examples.md)
* [安裝 Visual Studio 離線安裝所需的憑證](install-certificates-for-visual-studio-offline.md)
* [匯入或匯出安裝組態](import-export-installation-configurations.md)
* [Visual Studio Setup Archives](https://devblogs.microsoft.com/setup/tag/vs2017/) (Visual Studio 安裝封存)
* [Visual Studio 產品生命週期和服務](/visualstudio/releases/2019/servicing/)
* [同步的自動載入設定](../extensibility/synchronously-autoloaded-extensions.md)
