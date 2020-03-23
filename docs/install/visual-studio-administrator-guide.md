---
title: Visual Studio 系統管理員指南
titleSuffix: ''
description: 深入了解如何在企業環境中部署 Visual Studio。
ms.date: 03/09/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: bda9a73a7a1aabb2d288653ff4d7b20b1c40db8c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79190280"
---
# <a name="visual-studio-administrator-guide"></a>Visual Studio 系統管理員指南

在企業環境中，系統管理員通常會透過網路共用，或是使用系統管理軟體，將安裝部署給終端使用者。 我們已設計 Visual Studio 安裝程式引擎來支援企業部署，讓系統管理員可以建立網路安裝位置、預先設定安裝預設、在安裝程序期間部署產品金鑰，以及在成功推出後管理產品更新。

此系統管理員指南針對網路環境中的企業部署，提供以案例為基礎的指導方針。

## <a name="before-you-begin"></a>開始之前

為整個組織部署 Visual Studio 之前，有幾個要制訂之決策和完成的工作：

::: moniker range="vs-2019"

* 確認每部目標電腦都符合[基本安裝需求](/visualstudio/releases/2019/system-requirements/)。

* 決定您的服務需求。

  如果您的公司需要長時間使用功能集，但仍想要取得服務的定期更新，請計劃使用服務基準。 有關詳細資訊，請參閱[Visual Studio 產品生命週期和服務](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers)頁面中的 ***"企業和專業客戶支援"*** 部分，以及["如何在服務基準頁上更新 Visual Studio"。](update-servicing-baseline.md)

  如果您打算套用服務更新和累積的功能更新，您可以選擇最新版本。

* 決定更新模型。

  您希望個別用戶端電腦在何處取得更新？ 具體來說，請決定要從網際網路或從全公司的本機共用取得更新。 接著，如果您選擇使用本機的共用，請決定要由個別使用者更新自己的用戶端，或由系統管理員以程式設計方式更新用戶端。

* 決定您公司需要的[工作負載和元件](workload-and-component-ids.md?view=vs-2019)。

* 決定是否要使用[回應檔案](automated-installation-with-response-file.md?view=vs-2019) (可簡化指令碼檔案中的詳細資料管理作業)。

* 決定要啟用群組原則，還是要將 Visual Studio 設定為停用個別電腦上的客戶回函。

::: moniker-end

::: moniker range="vs-2017"

* 確認每部目標電腦都符合[基本安裝需求](/visualstudio/productinfo/vs2017-system-requirements-vs/)。

* 決定您的服務需求。

  如果您的公司需要長時間使用功能集，但仍想要取得服務的定期更新，請計劃使用服務基準。 有關詳細資訊，請參閱[Visual Studio 產品生命週期和服務](/visualstudio/releases/2019/servicing#support-for-older-versions-of-visual-studio)頁面的 Visual Studio 舊***版本的支援部分***，以及["如何在服務基準頁上更新 Visual Studio"。](update-servicing-baseline.md)

  如果您打算套用服務更新和累積的功能更新，您可以選擇最新版本。

* 決定更新模型。

  您希望個別用戶端電腦在何處取得更新？ 具體來說，請決定要從網際網路或從全公司的本機共用取得更新。 接著，如果您選擇使用本機的共用，請決定要由個別使用者更新自己的用戶端，或由系統管理員以程式設計方式更新用戶端。

* 決定您公司需要的[工作負載和元件](workload-and-component-ids.md?view=vs-2017)。

* 決定是否要使用[回應檔案](automated-installation-with-response-file.md?view=vs-2017) (可簡化指令碼檔案中的詳細資料管理作業)。

* 決定要啟用群組原則，還是要將 Visual Studio 設定為停用個別電腦上的客戶回函。

::: moniker-end

::: moniker range="vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>步驟 1 - 下載 Visual Studio 產品檔案

* [選取您想要安裝的工作負載和元件](workload-and-component-ids.md?view=vs-2019)。

* [建立 Visual Studio 產品檔案的網路共用](create-a-network-installation-of-visual-studio.md?view=vs-2019)。

## <a name="step-2---build-an-installation-script"></a>步驟 2 - 建置安裝指令碼

* 建置使用[命令列參數](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019)的安裝指令碼以控制安裝。

  >[!NOTE]
  > 您可以使用[回應檔案](automated-installation-with-response-file.md?view=vs-2019)來簡化指令碼。 請務必建立包含預設安裝選項的回應檔案。

* (選擇性) 在執行安裝指令碼時[套用大量授權產品金鑰](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019)，以讓使用者不需要另行啟用軟體。

* (選擇性) 更新網路配置以[控制產品更新傳遞至終端使用者的時間和來源位置](controlling-updates-to-visual-studio-deployments.md?view=vs-2019)。

* (選擇性) 設定會影響 Visual Studio 部署的登錄原則，例如要與其他版本或執行個體共用之部分套件的安裝位置、[快取套件的位置](set-defaults-for-enterprise-deployments.md?view=vs-2019)或[是否要快取套件](disable-or-move-the-package-cache.md?view=vs-2019)。

* (選擇性) 設定群組原則。 您也可以[將 Visual Studio 設定為停用個別電腦上的客戶意見反應](../ide/visual-studio-experience-improvement-program.md)。

## <a name="step-3---deploy"></a>步驟 3 - 部署

* 使用選擇的部署技術，在目標開發人員工作站上執行指令碼。

## <a name="step-4---deploy-updates"></a>步驟 4 - 部署更新

* 通過定期運行步驟 1 中使用的命令來添加更新的元件，使用 Visual Studio[的最新更新刷新網路位置](update-a-network-installation-of-visual-studio.md?view=vs-2019)。

  您可以使用更新指令碼來更新 Visual Studio。 為此，請使用[`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019)命令列參數。

## <a name="step-5---optional-use-visual-studio-tools"></a>步驟 5 - (選擇性) 使用 Visual Studio Tools

我們提供數種工具來協助您[偵測和管理用戶端電腦上已安裝的 Visual Studio 執行個體](tools-for-managing-visual-studio-instances.md?view=vs-2019)。

## <a name="advanced-configuration"></a>進階組態

預設情況下，Visual Studio 安裝允許從錯誤清單 F1 和代碼連結在必應搜索中包含自訂類型。 您可以配置 Visual Studio 以禁用搜索機制，禁止通過按策略更改以下登錄機碼的值來包括任何自訂使用者類型：

**"放置自訂類型 Bing 搜索" DWORD 0**

註冊表位於私有註冊表配置單元的 [軟體]微軟[VisualStudio]16.0\{實例 Id}>Roslyn_\*內部_診斷目錄中。 有關如何打開註冊表配置單元的說明，請參閱[編輯 Visual Studio 實例的註冊表](tools-for-managing-visual-studio-instances.md?view=vs-2019#editing-the-registry-for-a-visual-studio-instance)。

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>步驟 1 - 下載 Visual Studio 產品檔案

* [選取您想要安裝的工作負載和元件](workload-and-component-ids.md?view=vs-2017)。

* [建立 Visual Studio 產品檔案的網路共用](create-a-network-installation-of-visual-studio.md?view=vs-2017)。

## <a name="step-2---build-an-installation-script"></a>步驟 2 - 建置安裝指令碼

* 建置使用[命令列參數](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017)的安裝指令碼以控制安裝。

  >[!NOTE]
  > 您可以使用[回應檔案](automated-installation-with-response-file.md?view=vs-2017)來簡化指令碼。 請務必建立包含預設安裝選項的回應檔案。

* (選擇性) 在執行安裝指令碼時[套用大量授權產品金鑰](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017)，以讓使用者不需要另行啟用軟體。

* (選擇性) 更新網路配置以[控制產品更新傳遞至終端使用者的時間和來源位置](controlling-updates-to-visual-studio-deployments.md?view=vs-2017)。

* (選擇性) 設定會影響 Visual Studio 部署的登錄原則，例如要與其他版本或執行個體共用之部分套件的安裝位置、[快取套件的位置](set-defaults-for-enterprise-deployments.md?view=vs-2019)或[是否要快取套件](disable-or-move-the-package-cache.md?view=vs-2017)。

* (選擇性) 設定群組原則。 您也可以[將 Visual Studio 設定為停用個別電腦上的客戶意見反應](../ide/visual-studio-experience-improvement-program.md)。

## <a name="step-3---deploy"></a>步驟 3 - 部署

* 使用選擇的部署技術，在目標開發人員工作站上執行指令碼。

## <a name="step-4---deploy-updates"></a>步驟 4 - 部署更新

* 通過定期運行步驟 1 中使用的命令來添加更新的元件，使用 Visual Studio[的最新更新刷新網路位置](update-a-network-installation-of-visual-studio.md?view=vs-2017)。

  您可以使用更新指令碼來更新 Visual Studio。 為此，請使用[`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019)命令列參數。

## <a name="step-5---optional-use-visual-studio-tools"></a>步驟 5 - (選擇性) 使用 Visual Studio Tools

我們提供數種工具來協助您[偵測和管理用戶端電腦上已安裝的 Visual Studio 執行個體](tools-for-managing-visual-studio-instances.md?view=vs-2017)。

## <a name="advanced-configuration"></a>進階組態

預設情況下，Visual Studio 安裝允許從錯誤清單 F1 和代碼連結在必應搜索中包含自訂類型。 您可以配置 Visual Studio 以禁用搜索機制，禁止通過按策略更改以下登錄機碼的值來包括任何自訂使用者類型：

**"放置自訂類型 Bing 搜索" DWORD 0**

註冊表位於私有註冊表配置單元的 [軟體]微軟[VisualStudio]15.0\{實例 Id}>Roslyn_\*內部_診斷目錄中。 有關如何打開註冊表配置單元的說明，請參閱[編輯 Visual Studio 實例的註冊表](tools-for-managing-visual-studio-instances.md?view=vs-2017#editing-the-registry-for-a-visual-studio-instance)。

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [命令列參數範例](command-line-parameter-examples.md)
* [安裝 Visual Studio 離線安裝所需的憑證](install-certificates-for-visual-studio-offline.md)
* [匯入或匯出安裝組態](import-export-installation-configurations.md)
* [Visual Studio Setup Archives](https://devblogs.microsoft.com/setup/tag/vs2017/) (Visual Studio 安裝封存)
* [視覺化工作室產品生命週期和服務](/visualstudio/releases/2019/servicing/)
* [同步的自動載入設定](../extensibility/synchronously-autoloaded-extensions.md)
