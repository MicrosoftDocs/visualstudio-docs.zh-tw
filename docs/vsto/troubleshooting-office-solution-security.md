---
title: "Office 方案安全性疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: security [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2ab3571da02fa56cd905369ee44e372aedea4e36
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="troubleshooting-office-solution-security"></a>Office 方案安全性疑難排解
  本主題包含當您使用保護 Office 方案時，可能會遇到的常見問題的解決提示。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>無法從受限制的網站安裝方案的信任  
 使用者無法從 web 位置安裝方案，如果 Internet Explorer 受限制的網站區域中列出的網站。 即使方案以受信任的憑證簽署，也是如此。  
  
 部署資訊清單的 URL 可分類成五個區域的其中一個：  
  
-   我的電腦  
  
-   網際網路  
  
-   近端內部網路  
  
-   信任的網站  
  
-   受限制的網站  
  
 如果部署資訊清單的位置已被指派至受限制的網站區域，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]不會安裝方案。 如果已知位置，而且可以是受信任，使用者可以從限制的網站區域移除位置和安裝方案。 如需如何管理區域相關資訊，請參閱[設定 ClickOnce 信任的發行者](http://go.microsoft.com/fwlink/?LinkId=94774)。  
  
## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Internet Explorer 增強式安全性設定，或在安裝 Internet Explorer 7 時，無法從網路檔案共用或網路位置安裝方案  
 Internet Explorer 增強式安全性設定 （使用 ieesc 時） 在 Windows Server 2003 和更新版本，以及 Internet Explorer 7 及更新版本，會大幅限制使用者能夠瀏覽網際網路。 當使用者嘗試從網路檔案共用或 web 位置安裝 Office 方案時，它們可能會看到下列錯誤訊息: 「 此應用程式中的自訂功能將無法運作，因為憑證用來簽署部署資訊清單的*SolutionName*不受信任。 請連絡您的系統管理員尋求進一步的協助 」。  
  
 使用 ieesc 時與 Internet Explorer 7 及更新版本，如果部署資訊清單的 URL 分類的網際網路區域中，資訊清單必須來自受信任之發行者的憑證，或無法安裝方案。 未使用 ieesc 時，預設行為是提示使用者進行信任決策。  
  
 管理使用 ieesc 時，Internet Explorer 7 的效果和更新版本中，找出網站和通用命名慣例 (UNC) 路徑，您信任並將其加入至其中一個信任的安全性區域 （近端內部網路或信任的網站）。如需如何管理區域相關資訊，請參閱[設定 ClickOnce 信任的發行者](http://go.microsoft.com/fwlink/?LinkId=94774)。  
  
## <a name="see-also"></a>請參閱  
 [保護 Office 方案](../vsto/securing-office-solutions.md)  
  
  