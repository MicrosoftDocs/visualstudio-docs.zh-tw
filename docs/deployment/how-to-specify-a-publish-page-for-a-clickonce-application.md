---
title: 如何-指定 ClickOnce 應用程式的發佈頁面 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: acf7178a6b5456d048421533b8497682d69c2ee0
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381960"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>How to: Specify a publish page for a ClickOnce application (如何：指定 ClickOnce 應用程式的發行頁面)
發行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，會產生預設網頁（publish.htm），並與應用程式一起發行。 此頁面包含應用程式的名稱、安裝應用程式及（或）任何必要條件的連結，以及描述的說明主題連結 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 專案的 [**發行頁面**] 屬性可讓您指定應用程式的網頁名稱 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。

 一旦指定發行頁面之後，下次發佈時，它就會複製到發行位置;如果您再次發行，則不會覆寫此檔案。 如果您想要自訂網頁的外觀，您可以這麼做，而不必擔心遺失變更的情況。 如需詳細資訊，請參閱[如何：自訂 ClickOnce 預設網頁](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)。

 [發行]**頁面**屬性可以在 [**發行選項**] 對話方塊中設定，可從 [**專案設計**工具] 的 [**發行**] 窗格存取。

### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>若要指定 ClickOnce 應用程式的自訂網頁

1. 在**方案總管**中選取專案時，按一下 [**專案**] 功能表上的 [**屬性**]。

2. 選取 [**發行**] 窗格。

3. 按一下 [**選項**] 按鈕以開啟 [**發行選項**] 對話方塊。

4. 按一下 [部署]****。

5. 在 [**發行選項**] 對話方塊中，確定已選取 [**發行後開啟部署網頁**] 核取方塊（預設應加以選取）。

6. 在 [**部署網頁**] 方塊中，輸入您網頁的名稱，然後按一下 **[確定]**。

### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>若要防止每次發佈時都啟動 [發行] 頁面

1. 在**方案總管**中選取專案時，按一下 [**專案**] 功能表上的 [**屬性**]。

2. 選取 [**發行**] 窗格。

3. 按一下 [**選項**] 按鈕以開啟 [**發行選項**] 對話方塊。

4. 按一下 [部署]****。

5. 在 [**發行選項**] 對話方塊中，清除 [**發行後開啟部署網頁**] 核取方塊。

## <a name="see-also"></a>另請參閱
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [如何：使用發佈精靈發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [How to: Customize the ClickOnce default Web page](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md) (如何：自訂 ClickOnce 預設網頁)