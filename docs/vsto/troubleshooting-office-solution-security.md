---
title: 針對 Office 方案安全性進行疑難排解
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
ms.openlocfilehash: 76cd454cd66e31db8c521d71183aa479da1fe2a5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537406"
---
# <a name="troubleshoot-office-solution-security"></a>針對 Office 方案安全性進行疑難排解
  本主題包含的秘訣可解決當您使用保護 Office 方案時可能會遇到的常見問題。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>無法從受限制的網站安裝受信任的解決方案
 如果網站列在 Internet Explorer 的 [限制的網站] 區域中，使用者將無法從 web 位置安裝解決方案。 即使是使用受信任的憑證簽署解決方案，也是如此。

 部署資訊清單的 URL 可以分類為五個區域的其中一個：

- 我的電腦

- Internet

- 近端內部網路

- 信任的網站

- 限制的網站

  如果部署資訊清單的位置已指派給限制的網站區域，則不 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會安裝解決方案。 如果該位置是已知的，而且可以信任，則使用者可以從限制的網站區域中移除該位置，並安裝解決方案。 如需如何管理區域的詳細資訊，請參閱設定[ClickOnce 信任的發行者](/previous-versions/dotnet/articles/ms996418(v=msdn.10))。

## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>當安裝 Internet Explorer 增強式安全性設定或 Internet Explorer 7 時，無法從網路檔案共用或 web 位置安裝解決方案
 Internet Explorer 增強式安全性設定（IEESC）在 Windows Server 2003 和更新版本中，以及 Internet Explorer 7 及更新版本中，會大幅限制使用者流覽網際網路的能力。 當使用者嘗試從網路檔案共用或 web 位置安裝 Office 方案時，可能會收到下列錯誤訊息：「此應用程式中的自訂功能將無法運作，因為用來簽署*解決方案*的部署資訊清單的憑證不受信任。 請洽詢您的系統管理員以取得進一步的協助。」

 使用 IEESC 和 Internet Explorer 7 （含）以上版本時，如果部署資訊清單的 URL 分類于網際網路區域中，資訊清單必須擁有來自受信任發行者的憑證，否則無法安裝解決方案。 若沒有 IEESC，預設行為是提示使用者進行信任決策。

 若要管理 IEESC 和 Internet Explorer 7 及更新版本的效果，請識別您信任的網站和通用命名慣例（UNC）路徑，並將其新增至其中一個受信任的安全性區域（近端內部網路或信任的網站）。如需如何管理區域的詳細資訊，請參閱[設定 ClickOnce 信任的發行者](/previous-versions/dotnet/articles/ms996418(v=msdn.10))。

## <a name="see-also"></a>另請參閱
- [保護 Office 方案](../vsto/securing-office-solutions.md)
