---
title: 使用 Microsoft Endpoint Configuration Manager 啟用系統管理員更新 Visual Studio
titleSuffix: ''
description: 深入瞭解如何將系統管理員更新部署至 Visual Studio。
ms.date: 03/04/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 546fbad6-f12b-49cf-bccc-f2e63e051a18
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ae0bdde60cbf4c4c1eed00847c76ee797809b8db
ms.sourcegitcommit: 00e16b9afe6b22ba0591e4d0d92690544e6d4357
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2021
ms.locfileid: "105617321"
---
# <a name="enabling-administrator-updates-to-visual-studio-with-microsoft-endpoint-configuration-manager"></a>使用 Microsoft Endpoint Configuration Manager 啟用系統管理員更新 Visual Studio

Microsoft Endpoint Configuration Manager (SCCM) 可以使用軟體更新管理工作流程來管理 Visual Studio 2017 和 Visual Studio 2019 系統管理員更新。

> [!NOTE]
> 為了方便說明文件，下列內容會將 Visual Studio 2017 和 Visual Studio 2019 產品統稱為「Visual Studio」。

當 Microsoft 發佈新的 Visual Studio 更新至內容傳遞網路 (CDN) 時，Microsoft 會將對應的系統管理員更新套件同時發佈到 Microsoft Update 伺服器。 這樣就可以讓系統管理員透過 [Microsoft Update Catalog](https://www.catalog.update.microsoft.com/Home.aspx) (MUC) 或 [Windows Server Update Services](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) (WSUS) 來散發 Visual Studio 更新。 您可以設定設定管理員，將 Visual Studio 系統管理員更新從 WSUS 類別目錄同步處理至網站伺服器，然後下載更新並將其散發給整個組織的 Visual Studio 用戶端電腦。 如需 Visual Studio 的每個版本中有哪些修正程式的詳細資訊，請參閱 [版本](https://docs.microsoft.com/visualstudio/releases/2019/release-notes)資訊。 

若要透過設定管理員散發 Visual Studio 系統管理員更新，您必須採取下列兩個初始準備步驟： 
1. 啟用設定管理員以接收 Visual Studio 系統管理員更新通知。 
2. 啟用 (或停用) 用戶端電腦，以從設定管理員接收 Visual Studio 系統管理員更新。

執行這些步驟之後，您可以使用設定管理員的「軟體更新管理」功能來部署 Visual Studio 系統管理員更新。 「套用 [系統管理員更新](../install/applying-administrator-updates.md)」中說明 Visual Studio 系統管理員更新的不同類型和特性，其中提供如何及何時應將其散發至整個組織的指引。 如需設定管理員功能和選項的詳細資訊，請參閱 [Microsoft Endpoint Configuration Manager 中的部署軟體更新](https://docs.microsoft.com/mem/configmgr/sum/deploy-use/deploy-software-updates)。 

## <a name="enable-configuration-manager-to-receive-visual-studio-administrator-update-notifications"></a>啟用設定管理員以接收 Visual Studio 系統管理員更新通知 

若要讓設定管理員管理 Visual Studio 系統管理員更新，您將需要： 

* 目前執行的 Windows Server 授權版本 Microsoft Endpoint Configuration Manager (最新分支) 和 Windows Server Update Services (WSUS) 。 您無法使用 WSUS 本身來部署這些更新;必須搭配設定管理員使用。 

* 階層的頂層 WSUS 伺服器和頂層設定管理員網站伺服器必須能夠存取此處所列的 Visual Studio Url 和埠： [在防火牆或 proxy 伺服器後方安裝及使用 Visual Studio 和 Azure 服務](../install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)。  

* 當 Visual Studio 系統管理員更新套件可供使用時，必須將 Microsoft Endpoint Configuration Manager 設定為接收通知。  若要這樣做，請使用下列步驟，如需詳細資訊，請參閱 [Microsoft Endpoint Configuration Manager 中的軟體更新簡介](https://docs.microsoft.com/mem/configmgr/sum/understand/software-updates-introduction)。

  1. 在設定管理員主控台中，依序選取 [系統管理])  ([系統 **管理** ]，然後依序選取 [ **網站** 設定] ([左側]) [ **網站]，** 然後選取您的網站伺服器。 

  2. 在頂端的 [ **首頁** ] 索引標籤功能區中，選取 [ **設定** ] 群組按鈕中的 [設定 **網站元件**]，然後選取 [ **軟體更新點**]。 

  3. 在 [ **軟體更新點元件屬性** ] 對話方塊中： 

        * 在 [ **產品** ] 索引標籤的 [ **開發人員工具]、[運行** 時間] 和 [可轉散發階層] 下，選擇您想要同步處理的 Visual Studio 版本。   

        * 在 [ **分類** ] 索引標籤上，確認已選取 [安全性更新]、[Feature pack] 和 [更新]。   

  4. 接著，選擇 [ **軟體程式庫** ] (左下) ，然後在頂端的 [ **首頁** ] 索引標籤功能區中，選取 [ **同步處理軟體更新** ] 按鈕，以將軟體更新與 WSUS 伺服器同步處理。 同步處理軟體更新可讓您在設定管理員主控台中看到可用 Visual Studio 系統管理員更新，並且能夠從中部署。   

## <a name="enable-or-disable-client-machines-ability-to-receive-visual-studio-administrator-updates-from-configuration-manager"></a>啟用 (或停用) 用戶端電腦從設定管理員接收 Visual Studio 系統管理員更新的能力

若要讓用戶端電腦接受 Visual Studio 系統管理員更新，您必須確定 Visual Studio 用戶端偵測器公用程式已正確安裝，而且您將需要設定登錄機碼，才能讓用戶端接收系統管理員更新。  

### <a name="visual-studio-client-detector-utility"></a>Visual Studio 用戶端偵測器公用程式 

用戶端電腦必須安裝 Visual Studio 用戶端偵測器公用程式，才能正確地接收系統管理員更新。 此公用程式隨附于所有最近的 Visual Studio 版本。  

### <a name="encoding-administrator-intent-on-the-client-machines"></a>在用戶端電腦上編碼系統管理員意圖 

用戶端電腦必須啟用才能接收系統管理員更新。 需要執行此步驟，以確保不會不慎或不小心將更新推送到不小心的用戶端電腦。 

 **AdministratorUpdatesEnabled**   金鑰是專為系統管理員編碼系統管理員意圖所設計。 此索引鍵可以在任何標準 Visual Studio 位置中，如 Visual Studio 檔的 [企業部署設定預設值](https://docs.microsoft.com/visualstudio/install/set-defaults-for-enterprise-deployments) 中所述。 需要用戶端電腦上的系統管理員存取權，才能建立及設定此機碼的值。 

* 若要將用戶端電腦設定為接受系統管理員更新，請將 **AdministratorUpdatesEnabled**   REG_DWORD 機碼設定為 **1**。 
* 如果  **AdministratorUpdatesEnabled**   REG_DWORD 金鑰 **遺失或設為 0**，系統將會禁止系統管理員更新套用至用戶端電腦。 

## <a name="feedback-and-support"></a>意見反應與支援
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

您可以使用下列方法來提供有關 Visual Studio 系統管理員更新的意見反應，或回報影響更新的問題：
* 請參閱 [疑難排解 Visual Studio 安裝和升級問題](../install/troubleshooting-installation-issues.md) 的指引。
* 在 [視覺設定 Q&論壇](https://docs.microsoft.com/answers/topics/vs-setup.html)提出問題。
* 移至 [ [Visual Studio 支援] 頁面](https://visualstudio.microsoft.com/vs/support/)，並檢查問題是否列在常見問題中。  您也可以選取 [交談說明] 的 [ [支援連結](https://visualstudio.microsoft.com/vs/support/#talktous) ] 按鈕。
* [提供功能意見](https://aka.ms/vs/wsus/feedback) 反應，或向 Visual Studio 團隊回報問題，以獲得這項體驗。
* 洽詢您組織的 Microsoft 技術客戶經理。

## <a name="see-also"></a>另請參閱
* [套用系統管理員更新](../install/applying-administrator-updates.md)
* [Visual Studio 系統管理員指南](../install/visual-studio-administrator-guide.md)
* [Visual Studio 產品生命週期和服務](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs)
* [Visual Studio 2019 版本資訊](https://docs.microsoft.com/visualstudio/releases/2019/release-notes)
* [Visual Studio 2017 版本資訊](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes)
* [安裝 Visual Studio](../install/install-visual-studio.md)
* [Microsoft Update 目錄常見問題](https://www.catalog.update.microsoft.com/faq.aspx)
* [Microsoft Endpoint Configuration Manager (SCCM) 檔](https://docs.microsoft.com/mem/configmgr)
* [從 Microsoft Catalog 將更新匯入設定管理員](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Windows Server Update Services (WSUS) 檔](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
