---
title: Visual Studio 系統管理員指南
titleSuffix: ''
description: 深入了解如何在企業環境中部署 Visual Studio。
ms.date: 05/29/2018
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25bf36870e20b630c6de388c13f2b01bae4a274b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826396"
---
# <a name="visual-studio-2017-administrator-guide"></a>Visual Studio 2017 系統管理員指南

在企業環境中，系統管理員從網路共用或是使用系統管理軟體將安裝部署給終端使用者，是很常見的。 我們已設計 Visual Studio 安裝程式引擎來支援企業部署，讓系統管理員可以建立網路安裝位置、預先設定安裝預設值、在安裝程序期間部署產品金鑰，以及在成功推出後管理產品更新。 此系統管理員指南針對網路環境中的企業部署，提供以案例為基礎的指導方針。

## <a name="deploy-visual-studio-2017-in-an-enterprise-environment"></a>在企業環境中部署 Visual Studio 2017

只要每部目標電腦符合[最小安裝需求](/visualstudio/productinfo/vs2017-system-requirements-vs)，您就可以將 Visual Studio 2017 部署到用戶端工作站。 不論您是透過 System Center 這類軟體還是透過批次檔進行部署，一般都會想要執行下列步驟︰

1. 在網路位置[建立包含 Visual Studio 產品檔案的網路共用](create-a-network-installation-of-visual-studio.md)。

2. [選取您想要安裝的工作負載和元件](workload-and-component-ids.md)。

3. [建立回應檔](automated-installation-with-response-file.md)，其中包含預設安裝選項。 或者改為使用命令列參數[建置安裝指令碼](use-command-line-parameters-to-install-visual-studio.md)以控制安裝。

4. 在執行安裝指令碼時選擇性地[套用大量授權產品金鑰](automatically-apply-product-keys-when-deploying-visual-studio.md)，讓使用者不需要個別啟動軟體。

5. 更新網路配置以[控制產品更新傳遞至您使用者的時間](controlling-updates-to-visual-studio-deployments.md)。

6. (選擇性) 設定登錄機碼以[控制用戶端工作站上快取的項目](set-defaults-for-enterprise-deployments.md)。

7. 在目標開發人員工作站上，使用選擇的部署技術來執行在先前步驟產生的指令碼。

8. 定期執行您在步驟 1 所使用的命令來新增更新過的元件，以[使用 Visual Studio 最新更新來重新整理網路位置](update-a-network-installation-of-visual-studio.md)。

> [!IMPORTANT]
> 請注意，從網路共用安裝將會「記住」它們的來源位置。 這表示用戶端電腦的修復可能需要回到用戶端原先安裝開始處的網路共用。 請小心選擇網路位置，以便它能與您預期在組織中執行 Visual Studio 2017 用戶端的存留期一致。

## <a name="use-visual-studio-tools"></a>使用 Visual Studio Tools

我們提供數種工具來協助您[偵測和管理用戶端電腦上已安裝的 Visual Studio 執行個體](tools-for-managing-visual-studio-instances.md)。

> [!TIP]
> 除了系統管理員指南中的文件外，另外一個有關 Visual Studio 2017 安裝的實用資訊來源是 [Heath Stewart 的部落格](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/)。

## <a name="specify-customer-feedback-settings"></a>指定客戶回函設定

根據預設，Visual Studio 的安裝已啟用客戶回函。 當您啟用群組原則時，您可以設定 Visual Studio 停用個別電腦上的客戶回函。 若要這樣做，請在下列機碼上設定以登錄為基礎的原則：

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**

項目 = **OptIn**

值 = (DWORD)
* **0** 表示退出
* **1** 表示加入

如需客戶回函設定的詳細資訊，請參閱 [Visual Studio 客戶經驗改進計畫](../ide/visual-studio-experience-improvement-program.md)頁面。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio 2017](install-visual-studio.md)
* [使用命令列參數安裝 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
  * [命令列參數範例](command-line-parameter-examples.md)
  * [工作負載與元件識別碼參考](workload-and-component-ids.md)
* [建立 Visual Studio 的網路型安裝](create-a-network-installation-of-visual-studio.md)
  * [安裝 Visual Studio 離線安裝所需的憑證](install-certificates-for-visual-studio-offline.md)
* [使用回應檔將 Visual Studio 自動化](automated-installation-with-response-file.md)
* [部署 Visual Studio 時會自動套用產品金鑰](automatically-apply-product-keys-when-deploying-visual-studio.md)
* [設定 Visual Studio 企業部署的預設值](set-defaults-for-enterprise-deployments.md)
* [停用或移動套件快取](disable-or-move-the-package-cache.md)
* [更新 Visual Studio 的網路型安裝](update-a-network-installation-of-visual-studio.md)
* [控制 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)
* [用於偵測及管理 Visual Studio 執行個體的工具](tools-for-managing-visual-studio-instances.md)
