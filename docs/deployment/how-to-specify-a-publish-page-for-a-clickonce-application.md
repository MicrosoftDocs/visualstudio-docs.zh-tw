---
title: 如何： 指定 ClickOnce 應用程式的發行頁面 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 12a7d9dd2ad9d329fda5f27e78e24b0aa07cc3a6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598917"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>How to: Specify a publish page for a ClickOnce application (如何：指定 ClickOnce 應用程式的發行頁面)
發佈時[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式中，預設 Web 網頁 (publish.htm) 會產生並發佈以及應用程式。 此頁面包含的應用程式、 安裝應用程式和/或任何必要條件，連結和說明主題描述的連結名稱[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]。 **發行頁**專案的屬性可讓您指定網頁的名稱您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。

 一旦發佈頁面中有指定下, 一次發佈時，會將它複製到發行位置;它不會覆寫您在重新發佈。 如果您想要自訂頁面的外觀，您可以不必擔心會遺失您的變更。 如需詳細資訊，請參閱 <<c0> [ 如何： 自訂 ClickOnce 預設 Web 網頁](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)。

 **發行頁**屬性可以設定**發行選項**對話方塊中，從可存取**發行**窗格**專案設計工具**.

### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>若要指定自訂的網頁，ClickOnce 應用程式

1.  選取方案總管 中的專案，然後按一下 [專案]  功能表中的 [屬性] 。

2.  選取 **發佈**窗格。

3.  按一下 **選項** 按鈕以開啟**發行選項** 對話方塊。

4.  按一下 **部署**。

5.  在 **發行選項**對話方塊方塊中，請確定**發行之後開啟部署網頁**核取方塊已選取 （它應該預設會選取）。

6.  在 **部署網頁**方塊，可為您網頁中，輸入名稱，然後按一下**確定**。

### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>若要啟動每次您發行時，防止 [發行] 頁面

1.  選取方案總管 中的專案，然後按一下 [專案]  功能表中的 [屬性] 。

2.  選取 **發佈**窗格。

3.  按一下 **選項** 按鈕以開啟**發行選項** 對話方塊。

4.  按一下 **部署**。

5.  在 **發行選項**對話方塊中，清除**發行之後開啟部署網頁**核取方塊。

## <a name="see-also"></a>另請參閱
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [如何：使用發佈精靈發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [How to: Customize the ClickOnce default Web page](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md) (如何：自訂 ClickOnce 預設網頁)