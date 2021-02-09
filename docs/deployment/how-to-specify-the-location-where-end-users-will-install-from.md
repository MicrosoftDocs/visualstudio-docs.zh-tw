---
title: 指定終端使用者安裝來源的位置
description: 瞭解如何設定 [安裝 URL] 屬性，也就是裝載已發行 ClickOnce 應用程式以供安裝的位置。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 61c81ab15a3f4f6ec89d1b37a2c96d963bbdf67b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900412"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>How to: Specify the location where end users will install from (如何：指定終端使用者會從該處安裝的位置)

發佈 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，使用者前往下載和安裝應用程式的位置不一定是您最初發行應用程式的位置。 例如，在某些組織中，開發人員可能會將應用程式發佈到預備伺服器，然後系統管理員會將應用程式移至 Web 服務器。

在此情況下，您可以使用 `Installation URL` 屬性來指定使用者將前往以下載應用程式的網頁伺服器。 這是必要的，讓應用程式資訊清單知道要在哪裡尋找更新。

您 `Installation URL` 可以在 [**專案設計** 工具] 的 [**發行**] 頁面上設定屬性。

> [!NOTE]
> 您 `Installation URL` 也可以使用 **發行精靈** 來設定屬性。 如需詳細資訊，請參閱 [如何：使用發佈嚮導發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。

### <a name="to-specify-an-installation-url"></a>若要指定安裝 URL

1. 在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2. 按一下 [Publish (發行)]  索引標籤。

3. 在 [安裝 URL] 欄位中，使用格式的完整 URL 或使用格式的 UNC 路徑，輸入安裝位置 `https://www.contoso.com/ApplicationName` `\Server\ApplicationName` 。

## <a name="see-also"></a>另請參閱
- [How to: Specify where Visual Studio copies the files](../deployment/how-to-specify-where-visual-studio-copies-the-files.md) (如何：指定 Visual Studio 複製檔案的位置)
- [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [如何：使用發佈精靈發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)