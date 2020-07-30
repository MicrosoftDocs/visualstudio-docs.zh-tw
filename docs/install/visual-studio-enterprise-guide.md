---
title: Visual Studio enterprise 指南
description: 設定和疑難排解企業環境中的 Visual Studio。
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
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3d223d6e1e6ed3bf4b75b1c66bcc0f9dc897cfed
ms.sourcegitcommit: b8ce85a6d9c7fcceaad0fba625202f5ecf8f368c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2020
ms.locfileid: "87440672"
---
# <a name="visual-studio-enterprise-guide"></a>Visual Studio enterprise 指南
如果您想要節省時間，讓公司在 Visual Studio 上執行，請從這裡開始。 本企業指南包含的秘訣可協助您安裝和更新常見企業案例中的 Visual Studio、在遇到問題時解除封鎖，以及瞭解如何回報問題（如果您需要更多協助）。 

## <a name="get-started"></a>開始使用 
瞭解如何在網路和離線環境中將 Visual Studio 部署至您的企業。 

- **瞭解網路環境中的企業部署選項**。 《 [Visual Studio 系統管理員指南》](visual-studio-administrator-guide.md)提供了以案例為基礎的系統管理員指引。 

- **[取得疑難排解秘訣](troubleshooting-installation-issues.md)**。 當您安裝或更新 Visual Studio 時取得協助，並瞭解如何在您遭到封鎖時回報問題。 這些秘訣包含逐步指示，可解決大部分的線上或離線安裝問題。 

- **[建立 Visual Studio 的離線安裝](create-an-offline-installation-of-visual-studio.md)**。 如果您未連線到網際網路，或網際網路連線能力有限，請尋找安裝 Visual Studio 的選項。 

- **[建立](../deployment/creating-bootstrapper-packages.md)** 啟動載入器套件。 瞭解如何藉由建立產品和套件資訊清單來建立自訂啟動載入器套件。 

- **[部署 Visual Studio 時，自動套用產品金鑰](automatically-apply-product-keys-when-deploying-visual-studio.md)**。 您能以程式設計方式套用您的產品金鑰，作為用來自動化部署 Visual Studio 的一部分指令碼。 您可以在安裝 Visual Studio 期間或安裝完成之後，以程式設計方式在裝置上設定產品金鑰。 

## <a name="install-visual-studio"></a>安裝 Visual Studio 

瞭解如何在常見的企業案例中安裝 Visual Studio。 

- **[使用命令列參數來安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)**。 使用各種參數來控制或自訂您的 Visual Studio 安裝。 將安裝程式自動化，或建立安裝檔案的快取以供稍後使用。 

- **請參閱[Visual Studio 安裝的命令列參數範例](command-line-parameter-examples.md)**。 為了說明如何使用命令列參數來安裝 Visual Studio，請參閱您可以自訂的數個範例，以符合您的需求。 

- **[在防火牆或 proxy 伺服器後方安裝及使用 Visual Studio 和 Azure 服務](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)**。 如果您的組織使用防火牆或 proxy 伺服器等安全性措施，則您可能會想要新增至「允許清單」的網域 Url，以及您可能想要開啟的埠和通訊協定，讓您在安裝及使用 Visual Studio 和 Azure 服務時擁有最佳體驗。 

- **[建立 Visual Studio 的網路安裝](create-a-network-installation-of-visual-studio.md)**。 將初始安裝的檔案以及所有產品更新快取到單一資料夾。  

## <a name="update-visual-studio"></a>更新 Visual Studio 2017 

瞭解如何成功更新 Visual Studio 並修正更新問題。 

- **[更新 Visual Studio 的網路型安裝](update-a-network-installation-of-visual-studio.md)**。 使用最新的產品更新來更新 Visual Studio 的網路安裝配置，讓它可以做為最新 Visual Studio 更新的安裝點，同時維護已部署至用戶端工作站的安裝。

- **[在服務基準上更新 Visual Studio](update-servicing-baseline.md)**。 瞭解更新基準的價值，並瞭解次要版本與服務更新之間的差異。 

- **[使用最少的離線版面配置來更新 Visual Studio](update-minimal-layout.md)**。 對於未連線到網際網路的電腦，建立最基本的配置是更新離線 Visual Studio 實例的最簡單且最快速的方式。

- **[修復 Visual Studio](repair-visual-studio.md)以修正更新問題**。 有時您的 Visual Studio 安裝會損壞或損毀。 修復適用于修正所有安裝作業（包括更新）的安裝時間問題。 

- **遵循[Windows 安全性基準](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines)**。 Microsoft 致力於提供客戶安全的作業系統 (例如 Windows 10 和 Windows Server)，以及安全的應用程式 (例如 Microsoft Edge)。 除了其產品的安全性保證之外，Microsoft 也藉由提供各種設定功能，讓您可以精確控制您的環境。 

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱 

- [Visual Studio 的生產力指南](../ide/productivity-features.md)



