---
title: HOW TO：指定 ClickOnce 離線或線上安裝模式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bd0b985d7629ec282de4946ab89fef06e97c5921
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889010"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>HOW TO：指定 ClickOnce 離線或線上安裝模式
`Install Mode`針對[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式可讓您判斷應用程式是在離線或線上時使用。 當您選擇**應用程式只提供線上**，使用者必須能夠存取[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]發行 （網頁或檔案共用） 才能執行應用程式的位置。 當您選擇**應用程式也可以在離線時**，應用程式會將項目加入**開始**功能表並**新增或移除程式** 對話方塊中，使用者是無法在未連線時，執行應用程式。  
  
 `Install Mode`上，可以設定**發佈**頁面**專案設計工具**。  
  
 **附註**`Install Mode`也可以設定使用發佈精靈。 如需詳細資訊，請參閱[＜How to：使用 [發佈精靈] 發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>將 ClickOnce 應用程式提供線上只  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下 [發佈] 索引標籤。  
  
3.  在 **安裝模式和設定**區域中，按一下**應用程式只提供線上**選項按鈕。  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>若要使用 ClickOnce 應用程式線上或離線  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下 [發佈] 索引標籤。  
  
3.  在 **安裝模式和設定**區域中，按一下**應用程式也可以在離線時**選項按鈕。  
  
     應用程式安裝時，將項目加入**開始** 功能表並**新增或移除程式**控制項台中。  
  
## <a name="see-also"></a>另請參閱  
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用 [發佈精靈] 發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)