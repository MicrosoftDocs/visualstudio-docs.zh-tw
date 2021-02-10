---
title: Visual Studio 企業版指南
description: 在企業環境中設定 Visual Studio 並進行疑難排解。
ms.date: 07/29/2020
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
ms.openlocfilehash: e653d7ae5f2408fd8438cbdf69a28648c6bcc446
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967107"
---
# <a name="visual-studio-enterprise-guide"></a>Visual Studio 企業版指南
如果您想要在讓公司在 Visual Studio 上執行時節省時間，請從這裡開始。 本企業指南包含的秘訣可協助您在一般企業案例中安裝和更新 Visual Studio、在發生問題時解除封鎖，以及瞭解如何在您需要更多協助時回報問題。 

## <a name="get-started"></a>開始使用 
瞭解如何在網路和離線環境中將 Visual Studio 部署到您的企業。 

- **瞭解網路環境中企業部署的選項**。 《 [Visual Studio 系統管理員指南》](visual-studio-administrator-guide.md) 提供系統管理員以案例為基礎的指引。 

- **[取得疑難排解秘訣](troubleshooting-installation-issues.md)**。 當您在安裝或更新 Visual Studio 時取得說明，並瞭解如何在封鎖時回報問題。 這些秘訣包括應能解決大部分線上或離線安裝問題的逐步指示。 

- **[建立 Visual Studio 的離線安裝](create-an-offline-installation-of-visual-studio.md)**。 如果您未連線到網際網路或網際網路連線能力有限，請尋找安裝 Visual Studio 的選項。 

- **[建立](../deployment/creating-bootstrapper-packages.md)** 啟動載入器套件。 瞭解如何藉由建立產品和套件資訊清單來建立自訂啟動載入器套件。 

- **[部署 Visual Studio 時，自動套用產品金鑰](automatically-apply-product-keys-when-deploying-visual-studio.md)**。 您能以程式設計方式套用您的產品金鑰，作為用來自動化部署 Visual Studio 的一部分指令碼。 您可以在安裝 Visual Studio 期間或安裝完成之後，以程式設計方式設定裝置上的產品金鑰。 

## <a name="install-visual-studio"></a>安裝 Visual Studio 

瞭解如何在常見的企業案例中安裝 Visual Studio。 

- **[使用命令列參數來安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)**。 使用各種參數來控制或自訂您的 Visual Studio 安裝。 自動執行安裝程式，或建立安裝檔案的快取以供日後使用。 

- **請參閱 [Visual Studio 安裝的命令列參數範例](command-line-parameter-examples.md)**。 若要說明如何使用命令列參數來安裝 Visual Studio，請參閱您可以自訂以符合需求的數個範例。 

- **[在防火牆或 proxy 伺服器後方安裝及使用 Visual Studio 和 Azure 服務](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)**。 如果您的組織使用防火牆或 proxy 伺服器等安全性措施，則您可能會想要新增至「允許清單」的網域 Url，以及您可能想要開啟的埠和通訊協定，以便您在安裝和使用 Visual Studio 和 Azure 服務時獲得最佳體驗。 

- **[建立 Visual Studio 的網路安裝](create-a-network-installation-of-visual-studio.md)**。 將初始安裝的檔案以及所有產品更新快取到單一資料夾。  

## <a name="update-visual-studio"></a>更新 Visual Studio 2017 

瞭解如何成功更新 Visual Studio 並修正更新問題。 

- **[更新以網路為基礎的 Visual Studio 安裝](update-a-network-installation-of-visual-studio.md)**。 使用最新的產品更新來更新 Visual Studio 的網路安裝配置，使其可做為最新 Visual Studio 更新的安裝點，也能維護已部署至用戶端工作站的安裝。

- **[在維護基準上更新 Visual Studio](update-servicing-baseline.md)**。 瞭解在基準上更新的價值，並瞭解次要版本與服務更新之間的差異。 

- **[使用基本的離線版面配置來更新 Visual Studio](update-minimal-layout.md)**。 針對未連線到網際網路的電腦，建立最基本的版面配置是更新離線 Visual Studio 實例的最簡單且最快速的方式。

- **[修復 Visual Studio](repair-visual-studio.md) 以修正更新問題**。 有時您的 Visual Studio 安裝會損壞或損毀。 修復對於修正所有安裝作業（包括更新）的安裝時間問題很有用。 

- **遵循 [Windows 安全性基準](/windows/security/threat-protection/windows-security-baselines)**。 Microsoft 致力於提供客戶安全的作業系統 (例如 Windows 10 和 Windows Server)，以及安全的應用程式 (例如 Microsoft Edge)。 除了其產品的安全性保證之外，Microsoft 也藉由提供各種設定功能，讓您可以精確控制您的環境。 

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱 

- [Visual Studio 的生產力指南](../ide/productivity-features.md)