---
title: ClickOnce 應用程式的代碼啟用安全性 |Microsoft Docs
description: 瞭解 ClickOnce 應用程式的代碼啟用安全性，以及如何設定代碼啟用安全性許可權。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vb.XBAPProjectPropertiesSecurity.HowTo
- vb.XBAProjectPropertiesSecurity.HowTo
- vb.ProjectPropertiesSecurity.HowTo
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], security
- ClickOnce applications, caspol
- security [ClickOnce], WPF browser-hosted applications
- security [ClickOnce], ClickOnce applications
- ClickOnce applications, code access security policies
- security, ClickOnce
ms.assetid: 04b104d0-0bd3-4ccb-b164-1de92d234487
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4bf2977b3b6875a7dc38711b235f5848aa78559e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889157"
---
# <a name="code-access-security-for-clickonce-applications"></a>ClickOnce 應用程式的程式碼存取安全性
ClickOnce 應用程式是以 .NET Framework 為基礎，並且受限於程式碼存取安全性限制。 因此，您必須了解程式碼存取安全性的含意，並照著撰寫 ClickOnce 應用程式。

 程式碼存取安全性是 .NET Framework 中協助限制程式碼存取受保護資源和作業的一項機制。 您應該設定 ClickOnce 應用程式的程式碼存取安全性權限，以使用適合應用程式安裝程式位置的區域。 在大部分情況下，您可以選擇 [網際網路]  區域以獲得有限的權限集，或 [近端內部網路]  區域以獲得更高的權限集。

## <a name="default-clickonce-code-access-security"></a>預設 ClickOnce 程式碼存取安全性
 根據預設，ClickOnce 應用程式會在用戶端電腦上安裝或執行時獲得完全信任的權限。

- 具有完全信任權限的應用程式可以不受限制地存取資源，例如檔案系統和登錄。 這可能會允許您的應用程式 (和使用者的系統) 會遭到惡意程式碼入侵。

- 當應用程式需要完全信任權限時，可能會提示使用者將權限授與應用程式。 這表示應用程式無法真正提供 ClickOnce 經驗，而且提示可能會令較沒有經驗的使用者困惑。

  > [!NOTE]
  > 從卸除式媒體例如 CD-ROM 安裝應用程式時，不會提示使用者。 此外，網路系統管理員可以設定網路原則，以便在安裝來自信任來源的應用程式時，不會提示使用者。 如需詳細資訊，請參閱 [受信任的應用程式部署總覽](../deployment/trusted-application-deployment-overview.md)。

  若要限制 ClickOnce 應用程式的權限，您可以修改您應用程式的程式碼存取安全性權限，要求最符合應用程式所需權限的區域。 在大部分情況下，您可以選取要從中部署應用程式的區域。 例如，如果您的應用程式是企業應用程式，您可以使用 [近端內部網路]  區域。 如果您的應用程式是網際網路應用程式，您可以使用 [網際網路]  區域。

## <a name="configure-security-permissions"></a>設定安全性許可權
 您應該永遠設定 ClickOnce 應用程式來要求適當的區域，以限制程式碼存取安全性權限。 您可以在 [專案設計工具]  的 [安全性] 頁面上設定安全性權限。

 [專案設計工具]  中的 [安全性]  頁面包含 [啟用 ClickOnce 安全性設定]  核取方塊。 選取此核取方塊時，安全性權限要求會加入您應用程式的部署資訊清單。 在安裝期間，如果要求的權限超過從中部署應用程式之區域的預設權限，將會提示使用者授與權限。 如需詳細資訊，請參閱 [如何：啟用 ClickOnce 安全性設定](../deployment/how-to-enable-clickonce-security-settings.md)。

 從不同位置部署的應用程式會被授與不同層級的權限而不提示。 例如，從網際網路部署應用程式時，它就會獲得一組具有高度限制性的權限。 當從近端內部網路安裝時，它會獲得更多的權限，而從光碟安裝時，它會獲得完全信任權限。

 要開始設定權限時，您可以從 [安全性]  頁面上的 [區域]  清單選取安全性區域。 如果您的應用程式可能會從多個區域部署，請選取權限最低的區域。 如需詳細資訊，請參閱 [如何：設定 ClickOnce 應用程式的安全性區域](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)。

 可以設定的屬性會因權限集合而不同；並非所有的權限集合都具有可設定的屬性。 如需您的應用程式可以要求的完整權限清單的相關資訊，請參閱 <xref:System.Security.Permissions>。 如需如何設定自訂區域許可權的詳細資訊，請參閱 [如何：設定 ClickOnce 應用程式的自訂許可權](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)。

## <a name="debug-an-application-that-has-restricted-permissions"></a>對具有限制許可權的應用程式進行偵錯工具
 身為開發人員，您最可能以完全信任權限執行您的開發電腦。 因此，當您在偵錯應用程式時，看不到當使用者以受限制的權限執行時可能看到的相同安全性例外狀況。

 為了攔截這些例外狀況，您必須使用與使用者相同的權限來進行應用程式的偵錯。 權限受限制情況的偵錯可在 [專案設計工具]  的 [安全性] 頁面上啟用。

 當您以受限制的權限偵錯應用程式時，會針對尚未在 [安全性]  頁面上啟用的任何程式碼安全性要求引發例外狀況。 會出現例外狀況協助程式，提供有關如何修改程式碼來避免這個例外狀況的建議。

 此外，當您撰寫程式碼，程式碼編輯器中的 IntelliSense 功能將會停用已設定之安全性權限中不包含的任何成員。

 如需詳細資訊，請參閱 [How to: Debug a ClickOnce Application with Restricted Permissions](securing-clickonce-applications.md)。

## <a name="security-permissions-for-browser-hosted-applications"></a>瀏覽器裝載應用程式的安全性權限
 Visual Studio 針對 Windows Presentation Foundation (WPF) 應用程式提供下列專案類型：

- WPF Windows 應用程式

- WPF 網頁瀏覽器應用程式

- WPF 自訂控制項程式庫

- WPF 服務程式庫

  這些專案類型當中，只有 WPF 網頁瀏覽器應用程式裝載在網頁瀏覽器，並因此需要特殊的部署和安全性設定。 這些應用程式的預設安全性設定如下所示：

- **啟用 ClickOnce 安全性設定**

- **這是部分信任的應用程式**

- **網際網路區域** (並已選取 WPF 網頁瀏覽器應用程式的預設權限集合)

  在 [進階安全性設定]  對話方塊中，已選取並停用 [以選取的使用權限集合對此應用程式進行偵錯]  核取方塊。 這是因為無法針對瀏覽器裝載之應用程式關閉在區域中偵錯。

## <a name="see-also"></a>另請參閱
- [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)
- [How to: Enable ClickOnce security settings (如何：啟用 ClickOnce 安全性設定)](../deployment/how-to-enable-clickonce-security-settings.md)
- [如何：設定 ClickOnce 應用程式的安全性區域](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [How to: Set custom permissions for a ClickOnce application (如何：設定 ClickOnce 應用程式的自訂權限)](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [如何：使用受限制的許可權對 ClickOnce 應用程式進行 Debug 錯](securing-clickonce-applications.md)
- [信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)
- [專案設計工具、安全性頁](../ide/reference/security-page-project-designer.md)