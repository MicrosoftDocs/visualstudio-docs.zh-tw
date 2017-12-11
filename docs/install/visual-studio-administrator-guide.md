---
title: "Visual Studio 系統管理員指南 | Microsoft Docs"
description: "深入了解如何在企業環境中部署 Visual Studio。"
ms.custom: 
ms.date: 05/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 62e7a5cca98de8f4b584c7a3b3d9b72fdefa2519
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2017
---
# <a name="visual-studio-2017-administrator-guide"></a>Visual Studio 2017 系統管理員指南

在企業環境中，系統管理員從網路共用或是使用系統管理軟體將安裝部署給終端使用者，是很常見的。 我們已設計 Visual Studio 安裝程式引擎來支援企業部署，讓系統管理員可以建立網路安裝位置、預先設定安裝預設值、在安裝程序期間部署產品金鑰，以及在成功推出後管理產品更新。 此系統管理員指南針對網路環境中的企業部署，提供以案例為基礎的指導方針。

## <a name="deploying-visual-studio-2017-in-an-enterprise-environment"></a>在企業環境中部署 Visual Studio 2017

只要每部目標電腦符合[最小安裝需求](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)，您就可以將 Visual Studio 2017 部署到用戶端工作站。 不論您是透過 System Center 這類軟體還是透過批次檔進行部署，一般都會想要執行下列步驟︰

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

## <a name="visual-studio-tools"></a>Visual Studio Tools
我們提供數種工具來協助您[偵測和管理用戶端電腦上已安裝的 Visual Studio 執行個體](tools-for-managing-visual-studio-instances.md)。

> [!TIP]
> 除了系統管理員指南中的文件外，另外一個有關 Visual Studio 2017 安裝的實用資訊來源是 [Heath Stewart 的部落格](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/)。

## <a name="get-support"></a>取得支援
有時可能會發生一些問題。 如果您的 Visual Studio 安裝失敗，請參閱[針對 Visual Studio 2017 安裝和升級問題進行疑難排解](troubleshooting-installation-issues.md)頁面。 如果所有疑難排解步驟都沒有幫助，您可以透過即時聊天與我們連絡，以取得安裝協助 (僅限英文)。 如需詳細資訊，請參閱 [Visual Studio 支援頁面](https://www.visualstudio.com/vs/support/#talktous) \(英文\)。

以下是一些支援選項：
* 您可以透過 Visual Studio 安裝程式和 Visual Studio IDE 中的[回報問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)工具來向我們報告產品問題。
* 您可以在 [UserVoice](https://visualstudio.uservoice.com/forums/121579) 上與我們分享產品建議。
* 您可以在 [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/)追蹤產品問題，也可以在那裡詢問問題和尋找解答。
* 您也可以透過我們[在 Gitter 社群中的 Visual Studio 交談](https://gitter.im/Microsoft/VisualStudio)，與我們以及其他 Visual Studio 開發人員進行互動  (這個選項需要 [GitHub](https://github.com/) 帳戶)。

## <a name="see-also"></a>請參閱
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
