---
title: 作法：管理 ClickOnce 應用程式的更新 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Update
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, managing applications
- ClickOnce deployment, updates
- updating data, ClickOnce
- application updates
ms.assetid: a3f23f05-e7f1-4620-b23c-2d68f9643684
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ba899e922e98817462b06a1693525ab1ae69e20
ms.sourcegitcommit: a1e899248adaf104697fa7dea32a36e69e9cc119
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "71159907"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>作法：管理 ClickOnce 應用程式的更新
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式可以自動或以程式設計方式檢查更新。 身為開發人員，您有很多彈性可以指定執行更新檢查的時間和方式、是否需要更新，以及應用程式應該檢查更新的位置。

 您可以將應用程式設定為在應用程式啟動之前自動檢查更新，或在應用程式啟動後的設定間隔。 此外，您還可以指定所需的最低版本;也就是說，如果使用者的版本低於所需的版本，就會安裝更新。

 您可以將應用程式設定為根據事件（例如使用者要求）以程式設計方式檢查更新。 本主題中的「以程式設計方式檢查更新」程式會顯示如何撰寫使用<xref:System.Deployment.Application.ApplicationDeployment>類別的程式碼，以根據事件來檢查更新。

 您也可以從一個位置部署您的應用程式，並從另一個位置進行更新。 請參閱「若要指定不同的更新位置」程式。

 如需詳細資訊，請參閱[選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。

 您可以從 [**專案設計**工具] 的 [**發行**] 頁面，在 [**應用程式更新**] 對話方塊中管理更新行為。

### <a name="to-check-for-updates-before-the-application-starts"></a>在應用程式啟動前檢查更新

1. 在方案總管中選取專案之後，按一下 [專案] 功能表中 [屬性]。

2. 按一下 [發佈] 索引標籤。

3. 按一下 [**更新**] 按鈕以開啟 [**應用程式更新**] 對話方塊。

4. 在 [**應用程式更新**] 對話方塊中，確認已選取 [**應用程式應該檢查更新**] 核取方塊。

5. 在 [**選擇應用程式何時應檢查更新**] 區段中，選取 **[在應用程式啟動前**]。 這可確保連線到網路的使用者一律會以最新的更新來執行應用程式。

### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>在應用程式啟動之後，於背景檢查更新

1. 在方案總管中選取專案之後，按一下 [專案] 功能表中 [屬性]。

2. 按一下 [發佈] 索引標籤。

3. 按一下 [**更新**] 按鈕以開啟 [**應用程式更新**] 對話方塊。

4. 在 [**應用程式更新**] 對話方塊中，確認已選取 [**應用程式應該檢查更新**] 核取方塊。

5. 在 [**選擇應用程式何時應檢查更新] 區段**中，選取 **[在應用程式啟動後**]。 應用程式會以這種方式快速啟動，然後它會在背景中檢查更新，並只在有可用更新時通知使用者。 安裝之後，更新就不會生效，直到應用程式重新開機為止。

6. 在 [**指定應用程式應該檢查更新的頻率**] 區段中，選取 **[每次執行應用程式時檢查**] （預設值）或 [**檢查間隔**]，然後輸入數位和時間間隔。

### <a name="to-specify-a-minimum-required-version-for-the-application"></a>若要指定應用程式的最低必要版本

1. 在方案總管中選取專案之後，按一下 [專案] 功能表中 [屬性]。

2. 按一下 [發佈] 索引標籤。

3. 按一下 [**更新**] 按鈕以開啟 [**應用程式更新**] 對話方塊。

4. 在 [**應用程式更新**] 對話方塊中，確認已選取 [**應用程式應該檢查更新**] 核取方塊。

5. 選取 [**指定此應用程式的最低必要版本**] 核取方塊，然後輸入應用程式的**主要**、**次要**、**組建**和**修訂**編號。

### <a name="to-specify-a-different-update-location"></a>若要指定不同的更新位置

1. 在方案總管中選取專案之後，按一下 [專案] 功能表中 [屬性]。

2. 按一下 [發佈] 索引標籤。

3. 按一下 [**更新**] 按鈕以開啟 [**應用程式更新**] 對話方塊。

4. 在 [**應用程式更新**] 對話方塊中，確認已選取 [**應用程式應該檢查更新**] 核取方塊。

5. 在 [**更新位置**] 欄位中，輸入具有完整 URL 的更新位置、使用格式 *http://Hostname/ApplicationName* ，或使用格式 *\\ \Server\ApplicationName*的 UNC 路徑，或按一下 [**流覽]** 按鈕以流覽更新位置。

### <a name="to-check-for-updates-programmatically"></a>以程式設計方式檢查更新

1. 在方案總管中選取專案之後，按一下 [專案] 功能表中 [屬性]。

2. 按一下 [發佈] 索引標籤。

3. 按一下 [**更新**] 按鈕以開啟 [**應用程式更新**] 對話方塊。

4. 在 [**應用程式更新**] 對話方塊中，確認已清除 [**應用程式應該檢查更新**] 核取方塊。 （選擇性地，您可以選取此核取方塊，以程式設計方式檢查更新，並讓 ClickOnce 執行時間自動檢查更新）。

5. 在 [**更新位置**] 欄位中，輸入具有完整 URL 的更新位置、使用格式 *http://Hostname/ApplicationName* ，或使用格式 *\\ \Server\ApplicationName*的 UNC 路徑，或按一下 [**流覽]** 按鈕以流覽更新位置。 更新位置就是應用程式會在何處尋找其本身的更新版本。

6. 在 Windows Form 上建立按鈕、功能表項目或其他使用者介面專案，以供使用者選取以檢查更新。 從該專案的事件處理常式中，呼叫方法來檢查並安裝更新。 如需此方法C# [Visual Basic 的範例，請見如何：使用 ClickOnce 部署 API](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)以程式設計方式檢查應用程式更新。

7. 建立您的應用程式。

## <a name="see-also"></a>另請參閱
- <xref:System.Deployment.Application.ApplicationDeployment>
- [Application updates dialog box](/previous-versions/visualstudio/visual-studio-2010/axw1fa38(v=vs.100)) (應用程式更新對話方塊)
- [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [如何：使用 [發佈精靈] 發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [如何：使用 ClickOnce 部署 API 以程式設計的方式檢查應用程式更新](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)
