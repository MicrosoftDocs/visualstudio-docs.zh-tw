---
title: 針對 Office 方案安全性進行疑難排解
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 002759a1a5fd8a16ee3e7842df7439d6e6b9755f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862927"
---
# <a name="troubleshoot-office-solution-security"></a>針對 Office 方案安全性進行疑難排解
  本主題包含使用保護 Office 方案時，可能會遇到的常見問題的解決提示。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>無法從受限制的網站安裝受信任的方案  
 使用者無法安裝方案，從 web 位置，如果網站列為 Internet Explorer 受限制的網站區域中。 即使解決方案以受信任的憑證簽署，也是 true。  
  
 部署資訊清單的 URL 可以歸類為五個區域的其中一個：  
  
- 我的電腦  
  
- 網際網路  
  
- 近端內部網路  
  
- 信任的網站  
  
- 受限制的網站  
  
  部署資訊清單的位置已指派給限制的網站 區域中，如果[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]不會安裝方案。 如果已知位置，而且可以是受信任，使用者可以從受限制的網站區域移除位置和安裝解決方案。 如需有關如何管理區域的資訊，請參閱[設定 ClickOnce 受信任的發行者](http://go.microsoft.com/fwlink/?LinkId=94774)。  
  
## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>安裝 Internet Explorer 增強式安全性設定或 Internet Explorer 7 時，無法從網路檔案共用或 web 位置安裝解決方案  
 Internet Explorer 增強式安全性設定 （使用 ieesc 時） 在 Windows Server 2003 和更新版本，以及 Internet Explorer 7 及更新版本，會大幅限制使用者能夠瀏覽網際網路。 當使用者嘗試從網路檔案共用或網路位置安裝 Office 解決方案時，它們可能會收到下列錯誤訊息: 「 這個應用程式中的自訂功能將無法運作，因為使用憑證來簽署部署資訊清單，如*SolutionName*不受信任。 請連絡您的系統管理員以取得進一步協助。 」  
  
 使用 ieesc 時與 Internet Explorer 7 及更新版本，如果部署資訊清單的 URL 分類在網際網路區域中，資訊清單必須來自受信任之發行者的憑證，或無法安裝方案。 未使用 ieesc 時，預設行為是提示使用者進行信任決策。  
  
 若要管理使用 ieesc 時和 Internet Explorer 7 及更新版本中，找出網站和通用命名慣例 (UNC) 路徑，您信任，並將它們新增至其中一個受信任的安全性區域 （近端內部網路或信任的網站）。如需有關如何管理區域的資訊，請參閱[設定 ClickOnce 受信任的發行者](http://go.microsoft.com/fwlink/?LinkId=94774)。  
  
## <a name="see-also"></a>另請參閱  
 [保護 Office 方案](../vsto/securing-office-solutions.md)  
  
  