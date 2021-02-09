---
title: 選擇 ClickOnce 部署策略 |Microsoft Docs
description: 瞭解部署 ClickOnce 應用程式的策略，以及如何根據您要部署的應用程式類型來選擇策略。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, strategies
- deploying applications, ClickOnce
ms.assetid: 98bcab65-ab8b-4ed1-9adc-fdacf92b8106
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f4c20689c79529edf4a34edca857dedf1420b03f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895111"
---
# <a name="choose-a-clickonce-deployment-strategy"></a>選擇 ClickOnce 部署策略
有三種不同的策略可用來部署 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。您所選擇的策略主要是取決於您要部署的應用程式類型。 這三種部署策略說明如下：

- 從 Web 或網路共用安裝

- 從 CD 安裝

- 從 Web 或網路共用啟動應用程式

    > [!NOTE]
    > 除了選擇部署策略外，您也會想要選擇提供應用程式更新的策略。 如需詳細資訊，請參閱 [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。

## <a name="install-from-the-web-or-a-network-share"></a>從 Web 或網路共用安裝
 使用這項策略時，您的應用程式就會部署至 Web 伺服器或網路檔案共用。 當一般使用者想要安裝應用程式時，使用者會按一下 Web 網頁上的圖示，或按兩下檔案共用中的圖示。 然後就會在終端使用者電腦上下載、安裝並啟動應用程式。 [開始] 功能表和 [控制台] 的 [新增或移除程式] 中會新增一些項目。

 因為這項策略要依據網路連接而定，如果應用程式是要部署至具有區域網路或高速網際網路連接的使用者，則這類應用程式最適合使用這項策略。

 如果您要從 Web 部署應用程式，可以在使用 URL 啟用時傳遞引數給應用程式。 如需詳細資訊，請參閱 [如何：在線上 ClickOnce 應用程式中取得查詢字串資訊](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)。 您不能將引數傳遞給使用本文所述的其他任何方法所啟用的應用程式。

 若要在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中啟用這項部署策略，請按一下 [發佈精靈] 之 [如何安裝] 頁面上的 [從 Web] 或 [從 UNC 路徑或檔案共用]。

 這是預設的部署策略。

## <a name="start-the-application-from-the-web-or-a-network-share"></a>從 Web 或網路共用啟動應用程式
 這項策略類似第一項策略，不過此應用程式的行為會與 Web 應用程式一樣。 當使用這按一下 Web 網頁上的連結 (或按兩下檔案共用中的圖示) 時，就會啟動應用程式。 當使用者關閉應用程式時，該應用程式就無法在使用者的本機電腦上使用。而且 [開始] 功能表或 [控制台] 的 [新增或移除程式] 中不會新增任何項目。

> [!NOTE]
> 就技術上而言，應用程式會下載並安裝在本機電腦的應用程式快取中，就如同 Web 應用程式會下載至 Web 快取一樣。 與 Web 快取相同的是，檔案最後都會從應用程式快取中清除。 不過，在使用者的感覺上，應用程式是從 Web 或檔案快取執行的。

 這項策略最適合不常使用的應用程式，例如，通常一年只會執行一次的員工福利工具。

 若要在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中啟用這項部署策略，請按一下 [發佈精靈] 之 [從 Web 安裝或執行] 頁面上的 [不要安裝應用程式]。

 若要手動啟用這項部署策略，請變更部署資訊清單中的 [安裝] 標籤。 (這個標籤的值可以是 **true** 或 **false**。 在 *Mage.exe* 中，請使用 [應用程式類型] 清單中的 [僅限線上] 選項。)

## <a name="install-from-a-cd"></a>從 CD 安裝
 使用這項策略時，您的應用程式就會部署至卸除式媒體，例如 CD-ROM 或 DVD。 如同上一個選項，當使用者選擇安裝應用程式時，就會安裝並啟動應用程式，而且 [開始] 功能表和 [控制台] 的 [新增或移除程式] 中會新增一些項目。

 這項策略最適合將應用程式部署至沒有持續性 (Persistent) 網路連接或擁有低寬頻連接的使用者。 由於應用程式是從卸除式媒體安裝，所以不需要網路連接就可以進行安裝。不過，進行應用程式更新時仍然需要網路連接。

 若要在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中啟用這項部署策略，請按一下 [發佈精靈] 之 [如何安裝] 頁面上的 [從 CD-ROM 或 DVD-ROM]。

 若要手動啟用這項部署策略，請變更部署資訊清單中的 [deploymentProvider] 標籤。 (在 Visual Studio 中，這個屬性在專案設計工具的 [發佈] 頁面上公開為 [安裝 URL]。 在 *Mage.exe* 中，其為 [開始位置]。)

## <a name="web-browser-support"></a>Web 瀏覽器支援
 以 .NET Framework 3.5 為目標的應用程式可透過任何瀏覽器進行安裝。

 以 .NET Framework 2.0 為目標的應用程式則需要 Internet Explorer。

## <a name="see-also"></a>另請參閱
- [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)
- [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)
- [如何：使用發佈嚮導發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)