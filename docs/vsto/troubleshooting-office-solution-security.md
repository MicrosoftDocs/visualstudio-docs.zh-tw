---
title: 針對 Office 方案安全性進行疑難排解
description: 瞭解一些秘訣，以解決當您使用安全的 Microsoft Office 解決方案時可能會遇到的常見問題。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: troubleshooting
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 89ca980b378ee71d1db9b373459c8b7309f0ecc2
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97522893"
---
# <a name="troubleshoot-office-solution-security"></a>針對 Office 方案安全性進行疑難排解
  本主題包含的秘訣可解決您在使用保護 Office 方案時可能遇到的常見問題。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>受信任的解決方案無法從受限制的網站安裝
 如果網站列在 [Internet Explorer 限制的網站] 區域中，則使用者無法從 web 位置安裝解決方案。 即使是使用受信任的憑證簽署解決方案，也是如此。

 部署資訊清單的 URL 可分類為五個區域的其中一個：

- 我的電腦

- 網際網路

- 近端內部網路

- 信任的網站

- 限制的網站

  如果部署資訊清單的位置已指派給受限制的網站區域，則 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 不會安裝解決方案。 如果位置是已知的且可信任，則使用者可以從受限制的網站區域中移除位置，並安裝解決方案。 如需如何管理區域的詳細資訊，請參閱設定 [ClickOnce 受信任的發行者](/previous-versions/dotnet/articles/ms996418(v=msdn.10))。

## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>當 Internet Explorer 增強式安全性設定或安裝 Internet Explorer 7 時，無法從網路檔案共用或 web 位置安裝解決方案
 Internet Explorer 增強式安全性設定 (Windows Server 2003 和更新版本中的 IEESC) ，以及 Internet Explorer 7 和更新版本，會大幅限制使用者流覽網際網路的能力。 當使用者嘗試從網路檔案共用或 web 位置安裝 Office 方案時，可能會收到下列錯誤訊息：「此應用程式中的自訂功能將無法運作，因為用來簽署程式 *名稱* 的部署資訊清單的憑證不受信任。 請洽詢您的系統管理員以取得進一步的協助。」

 使用 IEESC 和 Internet Explorer 7 和更新版本時，如果部署資訊清單的 URL 分類在網際網路區域中，資訊清單必須有來自信任發行者的憑證，否則無法安裝解決方案。 若沒有 IEESC，預設行為是提示終端使用者進行信任決策。

 若要管理 IEESC 和 Internet Explorer 7 和更新版本的效果，請找出您信任 (UNC) 路徑的網站和通用命名慣例，並將其新增至 (近端內部網路或信任的網站) 的其中一個受信任的安全性區域。如需如何管理區域的詳細資訊，請參閱 [設定 ClickOnce 受信任的發行者](/previous-versions/dotnet/articles/ms996418(v=msdn.10))。

## <a name="see-also"></a>另請參閱
- [保護 Office 方案](../vsto/securing-office-solutions.md)
- [Visual Studio 疑難排解](/troubleshoot/visualstudio/welcome-visual-studio/)
