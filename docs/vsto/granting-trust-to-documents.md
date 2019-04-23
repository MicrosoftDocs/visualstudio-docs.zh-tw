---
title: 將信任授與文件
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: be8a17496788b0f4fe8abc9859b46cbfa11a6ed7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053009"
---
# <a name="grant-trust-to-documents"></a>將信任授與文件
  文件層級專案和應用程式層級專案具有相同的安全性需求：您需使用憑證簽署資訊清單，或按一下信任提示。 此外，文件或活頁簿所在的目錄，必須指定為信任位置。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="trusted-locations"></a>受信任的位置
 中的應用程式[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]和 Office 2010 皆有信任中心，讓使用者可以設定安全性和隱私權設定，例如受信任的位置。 Office 方案，在本機電腦會被視為受信任的位置。 不過，由於系統、每個使用者，以及 Internet Explorer 的暫存資料夾的特定目錄具有較高的風險性，因此可能無法受到信任。

 如需信任中心的詳細資訊，請參閱[安全性原則和設定 Office 2010 中的](http://go.microsoft.com/fwlink/?LinkId=89202)。 如需如何建立、 管理、 移除及設定信任的資料夾的詳細資訊，請參閱[2007 Office system 中設定受信任的位置和受信任的發行者設定](http://go.microsoft.com/fwlink/?LinkId=89203)和[建立、 移除或變更受信任的檔案位置](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62)。

## <a name="security-considerations-for-office-solutions"></a>Office 方案的安全性考量
 當您考慮要將資料夾加入信任位置時，有下列幾種安全性考量：

- 本機資料夾是被視為較安全並受到隱含信任的位置。 您必須將檔案共用等遠端位置指定為受信任的位置。

- 當您將目錄加入信任的位置時，這個動作不只會授與完全信任給 Office 方案，也會授與完全信任給 VBA 和 ActiveX 程式碼。 基於這個理由，根目錄並*我的文件*資料夾應該不會被指定為信任。

- 雖然文件本身是因為使用受信任的位置而受到信任，但仍需要額外的權限才能信任自訂項目。 您可以使用簽署資訊清單的憑證、 按一下信任提示，或安裝 Office 解決方案，以授與完全信任給自訂*Program Files*目錄。

- 您可將文件層級方案的文件或活頁簿儲存在組件的相同目錄中，或在不同的目錄中亦可。 例如，文件可能位於 SharePoint 伺服器上，而組件則位於網路檔案共用當中。 如需詳細資訊，請參閱[如何：使用 ClickOnce 將文件層級 Office 方案發行到 SharePoint 伺服器](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)。

## <a name="see-also"></a>另請參閱
- [授與信任給 Office 方案](../vsto/granting-trust-to-office-solutions.md)
- [針對 Office 方案安全性進行疑難排解](../vsto/troubleshooting-office-solution-security.md)
- [保護 Office 方案](../vsto/securing-office-solutions.md)
