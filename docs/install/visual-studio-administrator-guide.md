---
title: "Visual Studio 系統管理員指南 | Microsoft Docs"
description: "深入了解如何在企業環境中部署 Visual Studio。"
ms.custom: 
ms.date: 05/15/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
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
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: d9de84bed187c62962a76424aabdc5f355dff4dc
ms.openlocfilehash: 220b41f44cdc91ea84bf08b8eec8181dc01c25c7
ms.contentlocale: zh-tw
ms.lasthandoff: 05/15/2017

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

## <a name="see-also"></a>請參閱
* [安裝 Visual Studio 2017](install-visual-studio.md)
* [使用命令列參數安裝 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
  * [命令列參數範例](command-line-parameter-examples.md)
  * [工作負載與元件識別碼參考](workload-and-component-ids.md)
* [建立 Visual Studio 的網路型安裝](create-a-network-installation-of-visual-studio.md)
  * [在離線環境中安裝 Visual Studio 的特殊考量](install-visual-studio-in-offline-environment.md)
* [使用回應檔自動化 Visual Studio](automated-installation-with-response-file.md)
* [部署 Visual Studio 時會自動套用產品金鑰](automatically-apply-product-keys-when-deploying-visual-studio.md)
* [設定 Visual Studio 企業部署的預設值](set-defaults-for-enterprise-deployments.md)
* [停用或移動套件快取](disable-or-move-the-package-cache.md)
* [更新 Visual Studio 的網路型安裝](update-a-network-installation-of-visual-studio.md)
* [控制 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)
* [用於偵測及管理 Visual Studio 執行個體的工具](tools-for-managing-visual-studio-instances.md)
* [回報 Visual Studio 2017 的問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

