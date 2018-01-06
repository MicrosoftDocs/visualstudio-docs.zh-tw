---
title: "如何： 指定 ClickOnce 離線或線上安裝模式 |Microsoft 文件"
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
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: "8"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: b1c0f8615513639081351bdf77ea9ec63fc8309b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>如何：指定 ClickOnce 離線或線上安裝模式
`Install Mode`如[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式會決定應用程式可以在離線或在線上時使用。 當您選擇**應用程式僅提供線上**，使用者必須能夠存取[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]發行 （網頁或檔案共用） 才能執行應用程式的位置。 當您選擇**應用程式也可以在離線時**，應用程式將項目加入**啟動**功能表和**新增或移除程式**對話方塊; 使用者是無法在未連線時執行的應用程式。  
  
 `Install Mode`可以設定上**發行**頁面**專案設計工具**。  
  
 **請注意**`Install Mode`也可以設定使用發行精靈。 如需詳細資訊，請參閱[如何： 發行 ClickOnce 應用程式使用發行精靈](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>若要使用 ClickOnce 應用程式上線只  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下**發行** 索引標籤。  
  
3.  在**安裝模式和設定**區域中，按一下 **應用程式僅提供線上**選項按鈕。  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>若要使用 ClickOnce 應用程式上線或離線  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下**發行** 索引標籤。  
  
3.  在**安裝模式和設定**區域中，按一下 **應用程式也可以在離線時**選項按鈕。  
  
     應用程式安裝時，將項目加入**啟動**功能表和**新增或移除程式**控制台 中。  
  
## <a name="see-also"></a>請參閱  
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)