---
title: Visual Studio 企業版指南
description: 在企業環境中設定 Visual Studio 並進行疑難排解。
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e5e8a28ac89c2bea85aee8323060bf948266ad2e
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547384"
---
# <a name="visual-studio-enterprise-guide"></a>Visual Studio 企業版指南
如果您想要在讓公司在 Visual Studio 上執行時節省時間，請從這裡開始。 本企業指南包含的秘訣可協助您在一般企業案例中安裝和更新 Visual Studio、在發生問題時解除封鎖，以及瞭解如何在您需要更多協助時回報問題。 

## <a name="get-started"></a>開始使用 
瞭解如何在網路和離線環境中將 Visual Studio 部署到您的企業。

- **[使用 Microsoft Endpoint Configuration Manager (SCCM) 來啟用系統管理員更新](enabling-administrator-updates.md)**。  Visual Studio 更新包含在 [Microsoft Update 目錄](https://www.catalog.update.microsoft.com/Home.aspx) 和 [Windows Server Update Services (WSUS) ](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus)中。 然後，企業系統管理員可以使用標準部署工具（例如 Microsoft Endpoint Configuration Manager (SCCM) ）來下載更新，並將其散發至組織內 Visual Studio 用戶端電腦。

- **瞭解網路環境中企業部署的選項**。 《 [Visual Studio 系統管理員指南》](visual-studio-administrator-guide.md) 提供系統管理員以案例為基礎的指引。 

- **[取得疑難排解秘訣](troubleshooting-installation-issues.md)**。 當您在安裝或更新 Visual Studio 時取得說明，並瞭解如何在封鎖時回報問題。 這些秘訣包括應能解決大部分線上或離線安裝問題的逐步指示。 

- **[建立 Visual Studio 的離線安裝](create-an-offline-installation-of-visual-studio.md)**。 如果您未連線到網際網路或網際網路連線能力有限，請尋找安裝 Visual Studio 的選項。 

- **[建立](../deployment/creating-bootstrapper-packages.md)** 啟動載入器套件。 瞭解如何藉由建立產品和套件資訊清單來建立自訂啟動載入器套件。 

- **[部署 Visual Studio 時，自動套用產品金鑰](automatically-apply-product-keys-when-deploying-visual-studio.md)**。 您能以程式設計方式套用您的產品金鑰，作為用來自動化部署 Visual Studio 的一部分指令碼。 您可以在安裝 Visual Studio 期間或安裝完成之後，以程式設計方式設定裝置上的產品金鑰。 

## <a name="install-visual-studio"></a>安裝 Visual Studio 

瞭解如何在常見的企業案例中安裝 Visual Studio。 

- **[使用命令列參數來安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)**。 使用各種參數來控制或自訂您的 Visual Studio 安裝。 自動執行安裝程式，或建立安裝檔案的快取以供日後使用。 如需詳細資訊，請參閱 [命令列參數範例](command-line-parameter-examples.md)。

- **[建立 Visual Studio 的網路安裝](create-a-network-installation-of-visual-studio.md)**。 將初始安裝的檔案以及所有產品更新快取到單一資料夾。 

- **[在防火牆或 proxy 伺服器後方安裝及使用 Visual Studio 和 Azure 服務](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)**。 如果您的組織使用防火牆或 proxy 伺服器等安全性措施，則您可能會想要新增至「允許清單」的網域 Url，以及您可能想要開啟的埠和通訊協定，以便您在安裝和使用 Visual Studio 和 Azure 服務時獲得最佳體驗。 

- **[安裝離線安裝所需的憑證](../install/install-certificates-for-visual-studio-offline.md)**。 如果用戶端電腦完全中斷與網際網路的連線，請安裝必要的憑證。

## <a name="update-visual-studio"></a>更新 Visual Studio 2017 

瞭解如何成功更新 Visual Studio 並修正更新問題。 

- **[使用 Microsoft Endpoint Configuration Manager (SCCM) 來套用系統管理員更新](../install/applying-administrator-updates.md)**。 瞭解如何透過 SCCM 發佈 Visual Studio 功能、安全性和品質更新。 

- **[更新以網路為基礎的 Visual Studio 安裝](update-a-network-installation-of-visual-studio.md)**。 使用最新的產品更新來更新 Visual Studio 的網路安裝配置，使其可做為最新 Visual Studio 更新的安裝點，也能維護已部署至用戶端工作站的安裝。

- **[在維護基準上更新 Visual Studio](update-servicing-baseline.md)**。 瞭解在基準上更新的價值，並瞭解次要版本與服務更新之間的差異。 

- **[使用基本的離線版面配置來更新 Visual Studio](update-minimal-layout.md)**。 針對未連線到網際網路的電腦，建立最基本的版面配置是更新離線 Visual Studio 實例的最簡單且最快速的方式。

- **[修復 Visual Studio](repair-visual-studio.md) 以修正更新問題**。 有時您的 Visual Studio 安裝會損壞或損毀。 修復對於修正所有安裝作業（包括更新）的安裝時間問題很有用。 

- **遵循 [Windows 安全性基準](/windows/security/threat-protection/windows-security-baselines)**。 Microsoft 致力於提供客戶安全的作業系統 (例如 Windows 10 和 Windows Server)，以及安全的應用程式 (例如 Microsoft Edge)。 除了其產品的安全性保證之外，Microsoft 也藉由提供各種設定功能，讓您可以精確控制您的環境。 

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱 

- [Visual Studio 的生產力指南](../ide/productivity-features.md)

