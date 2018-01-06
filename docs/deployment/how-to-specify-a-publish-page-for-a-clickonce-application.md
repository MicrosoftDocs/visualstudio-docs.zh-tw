---
title: "如何： 指定 ClickOnce 應用程式的發行頁面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 491ef29c955c5ab06b8539ec5089f2ed32feaf36
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>如何：指定 ClickOnce 應用程式的發行頁面
發行時[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式中，產生並與應用程式發行預設網頁 (publish.htm)。 此頁面包含的應用程式、 安裝應用程式和/或任何必要條件，以及說明主題描述的連結名稱[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]。 **發行頁**為您的專案屬性可讓您指定的網頁名稱您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。  
  
 一旦已指定 [發行] 頁面，的下次當您發行時，會將它複製到發行位置。它不會覆寫您重新發行。 如果您想要自訂網頁的外觀，您可以這樣而不需擔心會遺失您的變更。 如需詳細資訊，請參閱[How to： 自訂 ClickOnce 預設 Web 網頁](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)。  
  
 **發行頁**屬性可以設定**發行選項**對話方塊中，從存取**發行**窗格**專案設計工具**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>若要指定自訂的 Web 網頁的 ClickOnce 應用程式  
  
1.  選取方案總管 中的專案，然後按一下 [專案]  功能表中的 [屬性] 。  
  
2.  選取**發行**窗格。  
  
3.  按一下**選項** 按鈕以開啟**發行選項** 對話方塊。  
  
4.  按一下**部署**。  
  
5.  在**發行選項**對話方塊方塊中，請確定**發行之後開啟部署網頁**選取核取方塊 （也應該選取依預設）。  
  
6.  在**部署網頁：**方塊中，輸入網頁的名稱，然後按一下**確定**。  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>若要防止啟動每次您發行的 [發行] 頁面  
  
1.  選取方案總管 中的專案，然後按一下 [專案]  功能表中的 [屬性] 。  
  
2.  選取**發行**窗格。  
  
3.  按一下**選項** 按鈕以開啟**發行選項** 對話方塊。  
  
4.  按一下**部署**。  
  
5.  在**發行選項**對話方塊中，清除**發行之後開啟部署網頁**核取方塊。  
  
## <a name="see-also"></a>請參閱  
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [如何： 自訂 ClickOnce 預設 Web 網頁](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)