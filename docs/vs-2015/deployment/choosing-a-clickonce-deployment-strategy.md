---
title: 選擇 ClickOnce 部署策略 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, strategies
- deploying applications, ClickOnce
ms.assetid: 98bcab65-ab8b-4ed1-9adc-fdacf92b8106
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 24eee31385ea2ef1c01924660e47e370fbed83f8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486020"
---
# <a name="choosing-a-clickonce-deployment-strategy"></a>選擇 ClickOnce 部署策略
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[選擇 ClickOnce 部署策略](https://docs.microsoft.com/visualstudio/deployment/choosing-a-clickonce-deployment-strategy)。  
  
有三種不同的策略可用來部署 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式。您所選擇的策略主要是取決於您要部署的應用程式類型。 這三種部署策略說明如下：  
  
-   從 Web 或網路共用安裝  
  
-   從 CD 安裝  
  
-   從 Web 或網路共用啟動應用程式  
  
    > [!NOTE]
    >  除了選擇部署策略外，您也會想要選擇提供應用程式更新的策略。 如需詳細資訊，請參閱 <<c0> [ 選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
## <a name="install-from-the-web-or-a-network-share"></a>從 Web 或網路共用安裝  
 使用這項策略時，您的應用程式就會部署至 Web 伺服器或網路檔案共用。 當一般使用者想要安裝應用程式時，使用者會按一下 Web 網頁上的圖示，或按兩下檔案共用中的圖示。 然後就會在終端使用者電腦上下載、安裝並啟動應用程式。 項目會加入**開始** 功能表並**新增或移除程式**中**控制台**。  
  
 因為這項策略要依據網路連接而定，如果應用程式是要部署至具有區域網路或高速網際網路連接的使用者，則這類應用程式最適合使用這項策略。  
  
 如果您要從 Web 部署應用程式，可以在使用 URL 啟用時傳遞引數給應用程式。 如需詳細資訊，請參閱 <<c0> [ 如何： 在線上 ClickOnce 應用程式中擷取查詢字串資訊](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)。 您不能將引數傳遞給使用本文所述的其他任何方法所啟用的應用程式。  
  
 若要啟用這項部署策略中的[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，按一下**從 Web**或是**從 UNC 路徑或檔案共用**上**安裝方式**頁面的 [發行精靈]。  
  
 這是預設的部署策略。  
  
## <a name="install-from-a-cd"></a>從 CD 安裝  
 使用這項策略時，您的應用程式就會部署至卸除式媒體，例如 CD-ROM 或 DVD。 如同前一個選項，當使用者選擇要安裝應用程式時，就會安裝並啟動，而項目會加入**開始** 功能表並**新增或移除程式**中**控制項面板**。  
  
 這項策略最適合將應用程式部署至沒有持續性 (Persistent) 網路連接或擁有低寬頻連接的使用者。 由於應用程式是從卸除式媒體安裝，所以不需要網路連接就可以進行安裝。不過，進行應用程式更新時仍然需要網路連接。  
  
 若要啟用這項部署策略中的[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，按一下**從 CD-ROM 或 DVD-ROM**上**安裝方式**頁面的 [發行精靈]。  
  
 若要手動啟用這項部署策略，請變更**deploymentProvider**部署資訊清單中的標記。 (在 Visual Studio 中，這個屬性會公開為**安裝 URL**上**發佈**頁面的 專案設計工具。 在 Mage.exe 中很**開始的位置**。)  
  
## <a name="start-the-application-from-the-web-or-a-network-share"></a>從 Web 或網路共用啟動應用程式  
 這項策略類似第一項策略，不過此應用程式的行為會與 Web 應用程式一樣。 當使用這按一下 Web 網頁上的連結 (或按兩下檔案共用中的圖示) 時，就會啟動應用程式。 當使用者關閉應用程式時，就無法再使用其本機電腦上，不會加入**開始** 功能表或**新增或移除程式**中**控制台**。  
  
> [!NOTE]
>  就技術上而言，應用程式會下載並安裝在本機電腦的應用程式快取中，就如同 Web 應用程式會下載至 Web 快取一樣。 與 Web 快取相同的是，檔案最後都會從應用程式快取中清除。 不過，在使用者的感覺上，應用程式是從 Web 或檔案快取執行的。  
  
 這項策略最適合不常使用的應用程式，例如，通常一年只會執行一次的員工福利工具。  
  
 若要啟用這項部署策略中的[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，按一下**不會安裝應用程式**上**安裝或執行從 Web**頁面的 [發行精靈]。  
  
 若要手動啟用這項部署策略，，請變更**安裝**部署資訊清單中的標記。 (其值可以是**真**或是**false**。 在 Mage.exe 中，使用**僅限線上**選項**應用程式類型**清單。)  
  
## <a name="web-browser-support"></a>Web 瀏覽器支援  
 以 .NET Framework 3.5 為目標的應用程式可透過任何瀏覽器進行安裝。  
  
 以 .NET Framework 2.0 為目標的應用程式則需要 Internet Explorer。  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)



