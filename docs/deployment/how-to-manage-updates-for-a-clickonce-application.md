---
title: HOW TO：管理 ClickOnce 應用程式的更新 |Microsoft Docs
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
ms.openlocfilehash: ed5ae8486ebede9db2ab6b052c1fed789883ceaf
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60051644"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>HOW TO：管理 ClickOnce 應用程式的更新
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式可以自動或以程式設計方式檢查更新。 身為開發人員，您會有更多的彈性，指定何時和如何執行更新檢查、 更新是否為必要項目，以及應用程式應該檢查更新。

 您可以設定應用程式的應用程式啟動後檢查更新會自動在應用程式啟動之前，或設定的間隔。 此外，您也可以指定最小必要的版本;也就是說，如果使用者的版本低於所需的版本，已安裝更新。

 您可以設定要檢查更新，例如使用者要求事件以程式設計方式為基礎的應用程式。 「 若要以程式設計方式檢查更新 」 的程序在本主題中會顯示如何撰寫使用程式碼<xref:System.Deployment.Application.ApplicationDeployment>事件為基礎來檢查是否有更新的類別。

 您也可以部署您的應用程式，從一個位置，然後從另一個更新。 請參閱 「 若要指定不同的更新位置。 」 的程序

 如需詳細資訊，請參閱[選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。

 在中管理更新行為**應用程式更新** 對話方塊中，可從**發佈**頁面**專案設計工具。**

### <a name="to-check-for-updates-before-the-application-starts"></a>應用程式啟動前，檢查有更新

1. 在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2. 按一下 [發佈] 索引標籤。

3. 按一下 **更新** 按鈕以開啟**應用程式更新** 對話方塊。

4. 在 **應用程式更新**對話方塊方塊中，請確定**應用程式應該檢查更新**選取核取方塊。

5. 在 **選擇此應用程式應該檢查更新**區段中，選取**應用程式啟動之前**。 這可確保一律連線到網路的使用者執行應用程式，使用最新的更新。

### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>在應用程式啟動之後，於背景檢查更新

1. 在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2. 按一下 [發佈] 索引標籤。

3. 按一下 **更新** 按鈕以開啟**應用程式更新** 對話方塊。

4. 在 **應用程式更新**對話方塊方塊中，請確定核取方塊**應用程式應該檢查更新**已選取。

5. 在 **選擇應用程式應該於何時檢查更新 」 一節**，選取**應用程式啟動後**。 應用程式會啟動更快速地如此一來，，然後它會檢查更新，在背景中，並有可用的更新時才會通知使用者。 安裝之後，更新不會影響應用程式重新啟動之前。

6. 在 **指定應用程式應該要檢查更新的頻率**區段中，選取**每次應用程式執行時檢查**（預設值） 或**檢查每個**然後輸入數字和時間間隔。

### <a name="to-specify-a-minimum-required-version-for-the-application"></a>若要指定應用程式的最小必要的版本

1. 在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2. 按一下 [發佈] 索引標籤。

3. 按一下 **更新** 按鈕以開啟**應用程式更新** 對話方塊。

4. 在 **應用程式更新**對話方塊方塊中，請確定**應用程式應該檢查更新**選取核取方塊。

5. 選取 **指定此應用程式的最小必要的版本**核取方塊，，然後輸入**主要**，**次要**，**建置**，以及**修訂**應用程式的數字。

### <a name="to-specify-a-different-update-location"></a>若要指定不同的更新位置

1. 在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2. 按一下 [發佈] 索引標籤。

3. 按一下 **更新** 按鈕以開啟**應用程式更新** 對話方塊。

4. 在 **應用程式更新**對話方塊方塊中，請確定**應用程式應該檢查更新**選取核取方塊。

5. 在 **更新位置**欄位中，輸入完整的 URL，並使用格式的更新位置*http://Hostname/ApplicationName*，或使用的格式將 UNC 路徑 *\\\Server\ApplicationName*，或按一下**瀏覽**按鈕來瀏覽的更新位置。

### <a name="to-check-for-updates-programmatically"></a>若要以程式設計方式檢查更新

1. 在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2. 按一下 [發佈] 索引標籤。

3. 按一下 **更新** 按鈕以開啟**應用程式更新** 對話方塊。

4. 在 **應用程式更新**對話方塊方塊中，請確定**應用程式應該檢查更新檔**核取方塊。 （或者，您可以選取此核取方塊，以檢查有更新，以程式設計的方式，也讓 ClickOnce 執行階段自動檢查更新。）

5. 在 **更新位置**欄位中，輸入完整的 URL，並使用格式的更新位置*http://Hostname/ApplicationName*，或使用的格式將 UNC 路徑 *\\\Server\ApplicationName*，或按一下**瀏覽**按鈕來瀏覽的更新位置。 更新位置就是應用程式將在其中尋找本身的更新版本。

6. 使用者會選取檢查更新的 Windows Form 上建立按鈕、 功能表項目或其他使用者介面項目。 從該項目的事件處理常式，呼叫方法來檢查並安裝更新。 您可以找到範例的 Visual Basic 和 VisualC#中的這類方法的程式碼[如何：檢查以程式設計方式使用 ClickOnce 部署 API 的應用程式更新](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)。

7. 建置您的應用程式。

## <a name="see-also"></a>另請參閱
- <xref:System.Deployment.Application.ApplicationDeployment>
- [Application updates dialog box](/previous-versions/visualstudio/visual-studio-2010/axw1fa38(v=vs.100)) (應用程式更新對話方塊)
- [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)
- [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [如何：使用 [發佈精靈] 發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [如何：使用 ClickOnce 部署 API 以程式設計的方式檢查應用程式更新](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)